# Walkthrough of how to take Landing Page and Put it on a Production Server

## Buying a Domain (GoDaddy, etc.)
## DigitalOcean Server Setup
## DigitalOcean Domain Setup
Right now we have a identifai.info domain registered for testing out new webpages and services! Fortunately, we already have this added to DigialOcean and set up with DigitalOcean nameservers so configuring the DNS (Domain Name Service) for the test landing page should be easy.
### Configuring in DigitalOcean
![alt text](docs/domainAdd.png)

## First Server Access
## SSL / HTTPS Configuration
## Firewall Setup
### Setting up UFW for SSH access, and public port 80 (HTTP) and 443 (HTTPS)

#### Check Status of UFW
```
sudo ufw status
```

#### Check Applications that you can add to the firewall
```
sudo ufw app list
```

#### Allow both HTTP and HTTPS
```
sudo ufw allow 'Nginx Full'
```

#### Allow SSH access before enabling
```
sudo ufw allow ssh
```

#### Enable UFW Firewall
```
sudo ufw enable
```

#### Check Status of Firewall
```
sudo ufw status
```

## FastAPI and Directory Setup

## Logging
When building a webserver for production-level use, you want to make sure that your endpoints have proper logging to track if there are any 
issues with a user accessing your page or if there is a user performing behavior on your page that is out of the ordinary. Because we are using
FastAPI and Python to spin up the webserver, we can start by logging outputs using the Python logging file! Here is a setup and short walkthrough that can help with this:

### Initial Setup
Basic setup for getting logging added to your FastAPI Application

```
import logging

logger = logging.getLogger('my_logger') # Give this a name that matches what exactly you are logging
logger.setLevel(logging.DEBUG)  # DEBUG captures all logging messages in the log file

fh = logging.FileHandler('app.log')
fh.setLevel(logging.DEBUG)

formatter = logging.Formatter('%(asctime)s - %(levelname)s - %(message)s') # This is the format of your log message in the file
fh.setFormatter(formatter)
logger.addHandler(fh)

```
### Logging Options

There are many different options in terms of severity when logging in Python! Below is a short breakdown.
```
logger.debug('This is a debug message')  # This will be logged to app.log
logger.info('This is an info message')   # This will be logged to app.log
logger.warning('This is a warning')      # This will be logged to app.log
logger.error('This is an error message') # This will be logged to app.log
logger.critical('Critical issue')        # This will be logged to app.log
```

### Where to implement
This is a sample endpoint to retrieve profile info from our API! See how we implement logging here
```
async def get_profile(token: str = Depends(oauth2_scheme)):

    """
    This endpoint allows you to retrieve information about your profile
    including: Username, Name, Organization, Industry, your Keywords, and
    your registration date.
    """

    await db.connect()

    username = get_username_from_token(token)
    if not username:
        logger.error("AUTHENTICATION ERROR: Invalid Token for retrieving profile information")
        raise HTTPException(status_code=401, detail="Invalid token")

    user = await user_db_obj.retrieve_user(username, db)
    if not user:
        raise HTTPException(status_code=404, detail="User not found")

    date_object = datetime.fromtimestamp(float(user["epochAdded"]))
    date_string = date_object.strftime('%Y-%m-%d %H:%M:%S.%f')

    user_obj = UserProfile(
        username=user["username"],
        name= user["name"],
        organization=user["organization"],
        industry=user["industry"],
        keywords=user["keywords"],
        regDate=date_string
    )

    logger.info("SUCCESS: Successfully retrieved profile information for: " + username)

    return user_obj

```
### What do the logs look like?
Sample from our API's app.log
```
2024-03-09 00:45:20,526 - ERROR - ERROR: One or more of the uploaded images had an incorrect number of faces for user: sampleAccount1
2024-03-09 01:36:55,771 - INFO - SUCCESS: Created access token and refresh token for: sampleAccount1
2024-03-09 01:37:24,286 - ERROR - Image filetype not supported for image querying by user: sampleAccount1
2024-03-09 01:37:44,171 - ERROR - Image filetype not supported for image querying by user: sampleAccount1
2024-03-09 01:41:03,848 - INFO - SUCCESS: Image was successfully queried by user: sampleAccount1
2024-03-09 01:41:24,477 - INFO - SUCCESS: Image was successfully queried by user: sampleAccount1
2024-03-09 01:41:33,904 - INFO - SUCCESS: Image was successfully queried by user: sampleAccount1
2024-03-09 01:41:43,832 - INFO - SUCCESS: Image was successfully queried by user: sampleAccount1
2024-03-09 01:41:53,812 - INFO - SUCCESS: Image was successfully queried by user: sampleAccount1
2024-03-09 01:42:13,932 - INFO - SUCCESS: Image was successfully queried by user: sampleAccount1
2024-03-09 01:42:23,666 - INFO - SUCCESS: Image was successfully queried by user: sampleAccount1
2024-03-09 01:42:33,754 - INFO - SUCCESS: Image was successfully queried by user: sampleAccount1
```

## Hosting first site!
