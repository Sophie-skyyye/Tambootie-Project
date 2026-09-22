<!--API Image-->
<script>
    import { onMount } from 'svelte';
    import { env } from '$env/dynamic/public';
  
    // @ts-ignore
    let cheetah = null;
     // @ts-ignore
    let tracking = null;
     // @ts-ignore
    let tree = null;
    const BASE_URL = 'https://api.unsplash.com/photos';
    const ACCESS_KEY = env.PUBLIC_UNSPLASH_ACCESS_KEY;
    const PHOTO_ID_CHEETAH = 'rt4dBZijxFY'; 
    const PHOTO_ID_TRACKING = '0LwfbRtQ-ac';
    const PHOTO_ID_TREE = '60XLoOgwkfA'

    // Function to handle form submission
  async function handleSubmit(event) {
    event.preventDefault();
    
    // Retrieve the email input value
    const formData = new FormData(event.target);
    const email = formData.get('email');
    
    // Example: Log the email address to the console
    console.log('Submitted email:', email);
  }

    onMount(async () => {
    try {
        const responseCheetah = fetch(`${BASE_URL}/${PHOTO_ID_CHEETAH}?client_id=${ACCESS_KEY}`);
        const responseTracking = fetch(`${BASE_URL}/${PHOTO_ID_TRACKING}?client_id=${ACCESS_KEY}`);
        const responseTree = fetch(`${BASE_URL}/${PHOTO_ID_TREE}?client_id=${ACCESS_KEY}`);
        const [dataCheetah, dataTracking, dataTree] = await Promise.all([responseCheetah, responseTracking, responseTree]);

        if (!dataCheetah.ok || !dataTracking.ok || !dataTree.ok) {
            throw new Error(`One or more images failed to load.`);
        }

        cheetah = await dataCheetah.json();
        tracking = await dataTracking.json();
        tree = await dataTree.json();
    } catch (error) {
        console.error('Error fetching images:', error);
    }
});
  </script>

<section class="container story1">
    <div class="text">
        <h3> From Dream to Reality: The Birth of Tambotie Wildlife Rehabilitation Center</h3>
        <p>In the heart of Hoedspruit, amidst the sprawling savannas and resilient tambotie trees, lies a sanctuary 
            born out of sheer passion and determination. The story begins with a humble farmer who, in 2016, discovered a
            tiny, helpless cheetah cub named Umfula. Little did he know, this encounter would change his life and spark 
            the creation of Tambotie Wildlife Rehabilitation Center.
    
            The founder, a lifelong wildlife enthusiast, faced numerous challenges while establishing the center. 
            From navigating bureaucratic red tape to securing funds, the journey was anything but easy. Yet, the 
            vision of a safe haven for injured and orphaned wildlife kept him going. After two grueling years of 
            hard work, Tambotie opened its doors on November 12, 2021, with Umfula as its first resident. 
            Today, the center stands as a testament to what unwavering dedication can achieve.</p>
    </div>
    <div class="image">
        {#if cheetah}
            <img src={cheetah.urls.regular} alt="cheetah" />
        {:else}
            <p>Loading...</p>
        {/if}
    </div>
</section>

<section class="container story2">
    <div class="text">
        <h3>Surviving the Drought: Stories from Tambotie</h3>
        <p>Hoedspruit’s droughts are relentless, testing the resilience of both flora and fauna. 
            During one particularly harsh drought in 2016, the landscape withered, and animals 
            struggled to find sustenance. The founder of Tambotie witnessed firsthand the desperation
            of wildlife, driving his determination to create a sanctuary.
            <br>
            At Tambotie, waterholes were built, and food troughs set up to support starving animals. 
            Stories of survival emerged, like the tale of a young giraffe that found refuge at the 
            center, and a pack of hyenas that thrived with the extra support. These experiences 
            underscored the critical role of rehabilitation centers in providing a lifeline during
            such tough times. Moving forward, Tambotie plans to expand its drought preparedness 
            efforts, ensuring they can support even more animals in need.</p>
    </div>
    <div class="image">
        {#if tree}
            <img src={tree.urls.regular} alt="tree" />
        {:else}
            <p>Loading...</p>
        {/if}
    </div>
</section>

<section class="container story3">
    <div class="text">
        <h3>Unlocking the Secrets of the Wild: Tracking Courses at Tambotie</h3>
        <p>At Tambotie, the art of tracking is not just a skill but a profound connection to the wild. 
            The center offers comprehensive tracking courses that teach participants to read the land and 
            understand the movements of its inhabitants. These courses cover everything from identifying 
            animal tracks and signs to understanding behavioral patterns.
            <br>
            Participants embark on hands-on experiences, guided by seasoned trackers who share their vast 
            knowledge and stories of the wild. Alumni of the program often speak of the transformative 
            impact it had on them, opening their eyes to the intricate web of life in the savanna. 
            If you’re looking to deepen your connection with nature and gain invaluable skills, Tambotie’s 
            tracking courses are a perfect adventure.</p>
    </div>
    <div class="image">
        {#if tracking}
            <img src={tracking.urls.regular} alt="tracking Image" />
        {:else}
            <p>Loading...</p>
        {/if}
    </div>
</section>

<section class="container story4">
    <div class="text">
        <h3> A Day in the Life: Volunteering at Tambotie</h3>
        <p>Volunteering at Tambotie is a unique blend of hard work and heartwarming moments. 
            Each day starts early, with volunteers preparing food and cleaning enclosures. 
            The morning might include feeding sessions, where you could find yourself 
            face-to-face with Umfula, the resident cheetah, or hand-feeding a group of 
            playful vervet monkeys.
    
            Afternoons are often dedicated to enrichment activities, ensuring the animals 
            remain mentally stimulated and happy. Volunteers share stories of unforgettable 
            experiences, like walking through the bush with Hamba, the baby rhino, or the 
            thrill of watching a rehabilitated bird take its first flight back into the wild. 
            It’s a demanding but deeply rewarding role, offering a unique chance to make a 
            tangible difference in the lives of these animals.</p>
    </div>
    <div class="image">
       
    </div>
</section>

<section class="userinput">
  <h3>Have a story to tell? Enter your email and we'll send you an application.</h3>

  <form on:submit={handleSubmit}>
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>

    <input type="submit" value="Submit">
  </form>
</section>


<style>
    .container {
    display: flex;
    flex-direction: row; /* Arrange flex items in a row */
    gap: 20px; /* Add 20px gap between flex items */
    margin-bottom: 20px;
}

.text {
    flex: 1; /* Allow the text section to grow and fill available space */
}

.image {
    flex: 1;
    display: flex;
    justify-content: center;  /* Center align items horizontally */
    align-items: center;
}

.image img {
    max-width: 100%; 
    max-height: 300px; /* Set maximum height for images */
    border-radius: 8px;
}

/* userinput */
.userinput{
    padding-top: 40px;
    padding-bottom: 40px;
}
.userinput form{
    text-align: center;
}

@media (max-width: 800px) {
    .textbox h1 {
        font-size: 20px; 
    }

    .textbox p {
        font-size: 10px; 
    }

    .container {
        flex-direction: column;  /* Stack flex items vertically */
    }
}

</style>
