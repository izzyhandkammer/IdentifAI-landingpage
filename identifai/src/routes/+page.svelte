<script>
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';
    import { Accordion, AccordionItem } from 'svelte-collapsible'

    import vidinter from '$lib/assets/videocallinterface.png';
    import evilinter from '$lib/assets/evilcall.png';
    import jmarciano from '$lib/assets/jmarciano.jpeg';
    import pvann from '$lib/assets/pvann.jpeg';
    let scroll;
    let image = vidinter;

    const updateImage = () => {
        if (scroll / document.body.offsetHeight > 0.75) {
            image = evilinter;
        } else {
            image = vidinter;
        }
    }

    onMount(() => {
        updateImage();
    });

    function smoothScroll(node) {
        node.addEventListener('click', event => {
            event.preventDefault();
            document.querySelector(event.target.hash).scrollIntoView({
                behavior: 'smooth'
            });
        });
    }

    const items = [
		{
			key: 'a',
			title: 'What is a deepfake?',
			text: 'A Deepfake is a manipulated video, photo, or audio recording that uses artificial intelligence (AI) to make it seem authentic. Deepfakes can be used to misinform users on social media sites, and can trigger reputation damage, financial loss, and legal issues.'
		},
		{
			key: 'b',
			title: 'What can I do to protect myself?',
			text: 'To safeguard yourself from the risks of deepfakes, adopting a proactive stance is key. At IdentifAI, we\'ve engineered a cutting-edge solution designed to actively protect and monitor the images you share online, ensuring your digital persona is secure from misuse and manipulation.'
		},
		{
			key: 'c',
			title: 'Why are deepfakes significant?',
			text: 'Deepfakes represent a significant concern in the digital age because they enable the creation of highly convincing yet false images and videos, undermining the ability to trust visual media and posing serious threats to personal reputation, security, and democratic processes. As these synthetic representations become increasingly indistinguishable from reality, they amplify the potential for misinformation, making the need for sophisticated detection and prevention methods more crucial than ever.'
		}
	]

</script>

<svelte:window bind:scrollY={scroll} />
<body>
    <div class="container"> 

        <div class="title">
            <h1 id="first-text">We are</h1>
            <h1 id="second-text"> IdentifAI.</h1>
        </div>
    
        <div class="rhetorical">
            <h2>How Many People Have Access to Your Pictures and Videos?</h2>
        </div>

        <div class="videocall">
            <img src={image} alt="Call" style="height: 500px"/>
            <p>this^ will be some kind of cool parallax animation trust me</p>
        </div>

        <div class="rhetorical">
            <h2>Deepfakes have become a significant threat to the fabric of our society that has become so intertwined with
                 the internet. That’s why IdentifAI seeks to create transparent internet in an age of ever-improving artificial 
                 intelligence.</h2>

            <p> more very dope animations and impressive stuff</p>

            <h2> We are currently in stealth, but please reach out or book time to discuss IdentifAI or your deepfake issues 
                with us below!</h2>
        </div> 

        <div id="about" class="about" style='padding-top: 4em;'>
            <h3 >Our Story</h3>
            <p> IdentifAI was inspired by Justin’s interest in digital authenticity and Paul’s cybersecurity expertise. 
                The two met at the University of Virginia and maintained their friendship post-graduation. After graduating,
                 Paul became a thought leader in generative AI and cyber. The two crossed paths again in San Francisco when
                  Paul spoke at the 2023 RSA conference. Realizing the synergy between blockchain’s value of authenticity 
                  and AI's capabilities, they decided to create IdentifAI. Justin saw beyond the speculative allure of NFTs 
                  and recognized the unsolved, pervasive issue blockchains have attempted to solve: the erosion of digital 
                  truth and authenticity. Paul saw beyond the immediate wonders of AI, grasping the ramifications to come. 
                  The two are now on a mission to protect businesses against the severe threats of deepfake attacks that can 
                  precipitate hefty financial losses and tarnish brand reputations, ensuring integrity remains at the forefront 
                  of the online experience.
            </p>

            <h3>Our Mission</h3>
            <p>IdentifAI takes a novel approach to address the challenge of deepfakes; our platform offers a streamlined 
                service for protecting, managing, and monitoring image veracity in real time for enterprises at high risk 
                of deepfake attacks.
            </p>
        

            <h3 id="team-heading" style='padding-top: 3em;'>Our Team</h3>
            <div id="our-team" class="our-team">
                    <div id="Justin" class="member">
                        <img src={jmarciano} alt="Justin Marciano" style="height: 250px; width: 250px; border-radius: 15%;"/>
                        <h4>Justin Marciano: Co-Founder</h4>
                        <p> Justin is the Co-Founder and CEO of IdentifAI. Studying economics with a concentration in finance at the
                            University of Virginia, he has navigated his way through the venture capital, blockchain, and payment 
                            sectors, aligning his career path with his enthusiasm for emerging technologies. Justin currently works
                            in product management and has previously worked at Stepstone Group as a VC & Growth Analyst.
                        </p>
                        <a class="linkedinlink" href="https://www.linkedin.com/in/justin-marciano32/" target="_blank">LinkedIn</a>
                    </div>

                    <div id="Paul" class="member">
                        <img src={pvann} alt="Paul Vann" style="height: 250px; width: 250px; border-radius: 15%;"/>
                        <h4>Paul Vann: Co-Founder</h4>
                        <p> Paul is a seasoned cybersecurity professional, with experience across numerous emerging markets in the 
                            field. He has worked at a wide array of cybersecurity and software development startups, helping to ensure
                            a more secure future for all. Paul additionally is passionate about emerging technologies in the space
                            and was recognized as a Top rated Speaker at the RSA Conference in 2023.
                        </p>
                        <a class="linkedinlink" href="https://www.linkedin.com/in/paul-vann-b996b2120/" target="_blank">LinkedIn</a>
                    </div>
            </div>
            <h3 id="contact" style='padding-top: 3em;'>Contact</h3>
            <p> We would love to hear from you! Reach out to us by filling out our form or schedule time with us via our Calendly.</p>

            <form id="fcf-form-id" class="fcf-form-class" method="post" action="contact-form-process.php">

                <div class="fcf-form-group">
                    <label for="Name" class="fcf-label">Your name</label>
                    <div class="fcf-input-group">
                        <input type="text" id="Name" name="Name" class="fcf-form-control" required>
                    </div>
                </div>

                <div class="fcf-form-group">
                    <label for="Email" class="fcf-label">Your email address</label>
                    <div class="fcf-input-group">
                        <input type="email" id="Email" name="Email" class="fcf-form-control" required>
                    </div>
                </div>
        
                <div class="fcf-form-group">
                    <label for="Message" class="fcf-label">Your message</label>
                    <div class="fcf-input-group">
                        <textarea id="Message" name="Message" class="fcf-form-control" rows="6" required></textarea>
                    </div>
                </div>
        
                <div class="fcf-form-group">
                    <button type="submit" id="fcf-button" class="fcf-btn fcf-btn-primary fcf-btn-lg fcf-btn-block">Send Message</button>
                </div>
                    
              </form>

            <div class="calendly-inline-widget" data-url="https://calendly.com/d/494-3xs-7yt/identifai-30-minute-meeting" style="min-width:320px;height:580px;"></div>
            <script type="text/javascript" src="https://assets.calendly.com/assets/external/widget.js" async></script>

            <div id="faq" style='padding-top: 3em;'>
                <h3>FAQ</h3>
                <div class="accordion">
                <Accordion>
                    { #each items as item }
                    <div class="pannel">
                        <AccordionItem key={item.key}>

                            <div slot='header' class='header'>
                                <div>
                                    <h2>{ item.title }</h2>
                                </div>
                            </div>
                            <p slot='body' class='body'>
                                { item.text }
                            </p>
                        </AccordionItem>                   
                    </div>
                    { /each }
                </Accordion>
                </div>
            </div>
        </div>

        
    </div>

        
</body>

<div id="menu">
    <div id="menuitems">
        <a href="#about" class="menu-item" use:smoothScroll>About</a>
        <a href="#our-team" class="menu-item" use:smoothScroll>Our Team</a>
        <a href="#contact" class="menu-item" use:smoothScroll>Contact</a>
        <a href="#faq" class="menu-item" use:smoothScroll>FAQ</a>
        <a href="https://identifai.substack.com/" target="_blank" class="menu-item">Blog</a>
    </div>
</div>



<style>
    * {
        transition: all 0.3s;
        background-color: #f1f7fe;
    }

    :global(html) {
    scroll-behavior: smooth;
    }

    h1 {
        font-size: 6em;
        font-weight: 700;
        margin: 0;
        padding: 0;
        position: center;
        top: 50%;
        left: 50%;
    }

    #first-text {
        animation: slideLeft 1s forwards;
    }

    #second-text {
        animation: fadein 2s forwards;
        color: #1F36E0;
        padding: 0 10px;
    }

    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: #f1f7fe;
        width: 60%;
        margin: 0 auto;
    }

    body {
        flex-direction: column;
        height: 100vh;
        background-color: #f1f7fe;
        margin: 0px;
        overflow: scroll;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        animation: blurFade 1s forwards;
    }


    @keyframes fadein {
        0% { opacity: 0; }
        50% { opacity: 0; }
        100% { opacity: 1; }
    }

    @keyframes slideLeft {
        0% { transform: translate(100%); }
        100% { transform: translate(0%); }
    }

    @keyframes blurFade {
        0% { filter: blur(75px); opacity: 0; }
        100% { filter: blur(0px); opacity: 1; }
    }

    .title{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        margin-top: 5%;
    }

    #menu {
        height: 60vh;
        align-items: center;
        position: fixed;
        top: 15em;
        left: 0;
        z-index: 10;
        animation: blurFade 1s forwards;
    }

    .menu-item {
        color: flex;
        font-size: 3em;
        display: block;
        text-decoration: none;
    }

    #menuitems {
        margin-left: 1em;    
    }

    #menuitems:hover > .menu-item {
        opacity: 0.3;
        font-size: 2em;
    }

    #menuitems:hover > .menu-item:hover {
        opacity: 1;
        font-size: 4em;
    }

    a:visited {
        color: #1F36E0;
    }

    .videocall {
        margin-top: 5%;
        display: block;
        object-fit: cover;
    }

    .videocall img {
        position: sticky;
    }

    .about {
        width: 90%;
    }

    p {
        font-size: 1.5em;
        line-height: 1.5em;
    }

    h3 {
        font-size: 3em;
        color: #1F36E0;
    }

    #team-heading {
        text-align: left;
        justify-self: left;
    }

    #our-team {
        display: flex;
        flex-direction: row;
        justify-content: center;
    }


    .linkedinlink {
        padding: 10px;
        margin: 10px;
        border-radius: 25px;
        border: #1F36E0 2px solid;
        color: #f1f7fe;
        background-color: #1F36E0;
        text-decoration: none;
        justify-self: center;
        font-size: 1em;
        display: inline-block;
    }
    
    .linkedinlink:hover {
        background-color: #f1f7fe;
        color: #1F36E0;
    }

    .linkedinlink:visited {
        color: #f1f7fe;
    }
    .linkedinlink:visited:hover {
        color: #1F36E0;
    }

    .member {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 2em;
    }

    .member p {
        font-size: 1.2em;
        line-height: 1.2em;
    }

    .accordion {
        display: flex;
        flex-direction: column;
        align-items: center;
        transition: 0.4s;
    }
    .header {
        background-color: aliceblue;
        font-size: large;
        color: #101B72;
    }
    .pannel {
        background-color: #f1f7fe;
        color: #101B72;
        border: #1F73E0 2px solid;
        border-radius: 20px;
        margin-bottom: 15px;
        padding: 10px;
    }
    .accordion .body{
        font-size: 1.5em;
        line-height: 1.5em;
        color: black;
    }
</style>