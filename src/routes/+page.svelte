<script lang="ts">
	// Components inlined — no external component imports or transitions
	import content from '$lib/data/content.json';
	import menusData from '$lib/data/menus.json';

	// Hero section images
	import heroImg from '$lib/assets/almaphotographyalma-7_1769639427309.jpg';
	import chefImg from '$lib/assets/retrato_1768838009913.webp';
	import impactImg from '$lib/assets/hojas_1768838009906.webp';
	import experiencesImg from '$lib/assets/manchas_1768838009910.webp';
	import valuesImg from '$lib/assets/img_9254_1769769809014.jpg';

	// Menu images
	import menu1Img from '$lib/assets/bowl__1768838009902.webp';
	import menu2Img from '$lib/assets/picada_1768838009912.webp';
	import menu3Img from '$lib/assets/cuadrados_1768838009904.webp';
	import menu4Img from '$lib/assets/plato_1768838009912.webp';

</script>

<svelte:head>
	<title>Atelier Tavola Viva - Art & Gastronomy</title>
</svelte:head>

<div class="min-h-screen font-sans">

<section
  id="hero"
  class="relative min-h-screen w-full flex items-center justify-center bg-cover bg-center bg-no-repeat"
  style={`background-image: url(${heroImg});`}
>

  <div class="absolute backdrop-blur-xs inset-0 bg-black/40"></div>

  <!-- Content -->
  <div class="relative z-10 max-w-4xl px-6 text-center text-white">
    <h1 class="text-6xl md:text-6xl font-light tracking-tight mb-6">
      Art &amp; Gastronomy, Connecting on the Tavola Viva
    </h1>

    <p class="text-xl md:text-xl leading-relaxed opacity-90">
      A private chef service and workshop platform focused on physical and mental
      well-being through the synergy of visual arts and cooking.
    </p>
  </div>
</section>

<section id="about" class="w-full bg-white py-20">
  <div class="max-w-6xl mx-auto px-6 grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
    
    <!-- Image -->
    <div class="w-full h-full">
      <div class="aspect-[3/4] w-full overflow-hidden rounded-2xl shadow-lg">
        <img
          src={chefImg}
          alt="Portrait of Alma"
          class="w-full h-full object-cover"
        />
      </div>
    </div>

    <!-- Text content -->
    <div>
      <span class="text-orange-500 uppercase tracking-wide text-sm">
        The Artist
      </span>

      <h2 class="text-3xl md:text-4xl font-light mt-2 mb-6">
        Alma, From Patagonia to the World
      </h2>

      <div class="space-y-4 text-gray-700 leading-relaxed">
        <p>
          Born amidst the rugged winds and vast landscapes of Argentine Patagonia,
          my journey began with a deep appreciation for nature's raw beauty.
          I graduated in Visual Arts from the Universidad Nacional de Córdoba (UNC),
          a foundation that has traveled with me across oceans and cultures.
        </p>

        <p>
          My path led me to Ireland's green hills, Amsterdam's artistic canals,
          and finally to Italy's culinary heart. Each place added a layer to my
          identity as a visual artist and chef, complemented by my certification
          in Art Therapy and rigorous HACCP food safety standards.
        </p>

        <p>
          With years of experience in gastronomy, photography, and illustration,
          I weave these disciplines together. My food is not just eaten; it is
          experienced visually and emotionally, creating a bridge between the
          plate and the soul.
        </p>
      </div>

      <!-- Stats -->
      <div class="mt-10 flex gap-10">
        <div>
          <span class="text-4xl font-light text-orange-500">15+</span>
          <p class="text-sm text-gray-600 mt-1">Years Experience</p>
        </div>

        <div>
          <span class="text-4xl font-light text-orange-500">4</span>
          <p class="text-sm text-gray-600 mt-1">Countries Lived</p>
        </div>
      </div>
    </div>

  </div>
</section>

<section id="philosophy" class="w-full bg-neutral-50 py-24">
  <div class="max-w-6xl mx-auto px-6 space-y-24">

    <!-- Philosophy block -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
      
      <!-- Text -->
      <div>
        <span class="text-orange-500 uppercase tracking-wide text-sm">
          My Philosophy
        </span>

        <h2 class="text-3xl md:text-4xl font-light mt-2 mb-6">
          Nourishing Body &amp; Soul
        </h2>

        <h3 class="text-lg font-medium text-gray-800 mb-4">
          The Synergy of Art &amp; Wellness
        </h3>

        <div class="space-y-4 text-gray-700 leading-relaxed">
          <p>
            I believe that true well-being comes from a holistic balance.
            There is a profound connection between what we see, what we eat,
            and how we feel.
          </p>

          <p>
            Art stimulates the mind, nutrition fuels the body, and connection
            nourishes the spirit.
          </p>

          <p>
            By integrating visual arts with conscious gastronomy, we create a
            sanctuary for the senses. This synergy forms the foundation for
            balanced well-being, inviting you to slow down, appreciate beauty
            in the details, and reconnect with yourself and others in a
            meaningful way.
          </p>
        </div>
      </div>

      <!-- Image -->
      <div class="w-full">
        <div class="aspect-[4/5] w-full overflow-hidden rounded-2xl shadow-lg">
          <img
            src={valuesImg}
            alt="Nature textures and organic details"
            class="w-full h-full object-cover"
          />
        </div>
      </div>
    </div>

    <!-- Values block -->
    <div>
      <div class="max-w-3xl mb-12">
        <h3 class="text-2xl md:text-3xl font-light mb-4">
          Sustainability
        </h3>
        <p class="text-gray-700 leading-relaxed">
          Every choice we make in the kitchen is an opportunity to care for the
          planet. From sourcing to serving, sustainability guides our practice.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-10">
        
        <div>
          <h4 class="text-lg font-medium text-orange-500 mb-2">
            Local &amp; Seasonal
          </h4>
          <p class="text-gray-700 leading-relaxed">
            Sourcing ingredients from local farmers and producers, respecting
            the natural rhythm of the seasons.
          </p>
        </div>

        <div>
          <h4 class="text-lg font-medium text-orange-500 mb-2">
            Zero Waste
          </h4>
          <p class="text-gray-700 leading-relaxed">
            Minimizing waste through thoughtful planning, composting, and
            creative use of every ingredient.
          </p>
        </div>

        <div>
          <h4 class="text-lg font-medium text-orange-500 mb-2">
            Conscious Choices
          </h4>
          <p class="text-gray-700 leading-relaxed">
            Prioritizing organic, ethically-sourced products that honor both
            the earth and the people who cultivate it.
          </p>
        </div>

      </div>
    </div>

  </div>
</section>

<section id="offerings" class="w-full bg-white py-24">
  <div class="max-w-7xl mx-auto px-6">

    <!-- Section header -->
    <div class="max-w-3xl mb-16">
      <span class="text-orange-500 uppercase tracking-wide text-sm">
        Offerings
      </span>

      <h2 class="text-3xl md:text-4xl font-light mt-2">
        Curated Culinary Journeys
      </h2>
    </div>

    <!-- Cards -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-10">
      
      <!-- Card 1 -->
      <div class="group">
        <div class="aspect-[4/5] w-full overflow-hidden rounded-2xl mb-4">
          <img
            src={menu1Img}
            alt="Healthy Anti-inflammatory menu"
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
          />
        </div>
        <h3 class="text-lg font-medium mb-2">
          Healthy Anti-inflammatory
        </h3>
        <p class="text-gray-700 leading-relaxed text-sm">
          A restorative menu focused on gut health and reducing inflammation,
          featuring vibrant vegetables, omega-3 rich ingredients, and healing
          spices.
        </p>
      </div>

      <!-- Card 2 -->
      <div class="group">
        <div class="aspect-[4/5] w-full overflow-hidden rounded-2xl mb-4">
          <img
            src={menu2Img}
            alt="Creative Aperitif menu"
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
          />
        </div>
        <h3 class="text-lg font-medium mb-2">
          Creative Aperitif
        </h3>
        <p class="text-gray-700 leading-relaxed text-sm">
          An artistic selection of small bites designed to spark conversation.
          Unexpected pairings, textures, and visual delight in every piece.
        </p>
      </div>

      <!-- Card 3 -->
      <div class="group">
        <div class="aspect-[4/5] w-full overflow-hidden rounded-2xl mb-4">
          <img
            src={menu3Img}
            alt="Finger Foods menu"
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
          />
        </div>
        <h3 class="text-lg font-medium mb-2">
          Finger Foods
        </h3>
        <p class="text-gray-700 leading-relaxed text-sm">
          Elegant, easy-to-eat creations perfect for mingling. A journey of
          flavors that fits in the palm of your hand without compromising on
          sophistication.
        </p>
      </div>

      <!-- Card 4 -->
      <div class="group">
        <div class="aspect-[4/5] w-full overflow-hidden rounded-2xl mb-4">
          <img
            src={menu4Img}
            alt="Local classics with a twist menu"
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
          />
        </div>
        <h3 class="text-lg font-medium mb-2">
          Local Classics with a Twist
        </h3>
        <p class="text-gray-700 leading-relaxed text-sm">
          Honoring traditional recipes while reinventing them with modern
          techniques and artistic presentation. Nostalgia meets innovation.
        </p>
      </div>

    </div>
  </div>
</section>

<section
  id="experiences"
  class="relative w-full py-28 bg-cover bg-center bg-no-repeat"
  style={`background-image: url(${experiencesImg});`}
>
  <!-- Overlay -->
  <div class="absolute inset-0 bg-black/70 backdrop-blur-md"></div>

  <!-- Content -->
  <div class="relative z-10 max-w-6xl mx-auto px-6 text-white">

    <!-- Header -->
    <div class="max-w-3xl mb-16">
      <span class="text-orange-400 uppercase tracking-wide text-sm">
        Experiences
      </span>

      <h2 class="text-3xl md:text-4xl font-light mt-2 mb-6">
        Creative Workshops
      </h2>

      <p class="text-white/85 leading-relaxed">
        Immerse yourself in a hands-on exploration of creativity. Our workshops
        blend visual arts techniques with culinary skills, teaching you to see
        ingredients as a palette and the plate as a canvas.
      </p>
    </div>

    <!-- Cards -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-10">

      <!-- Card 1 -->
      <div class="bg-white/10 backdrop-blur-lg rounded-2xl p-8">
        <h3 class="text-xl font-medium text-orange-400 mb-4">
          Visual Arts
        </h3>
        <p class="text-white/85 leading-relaxed">
          Explore illustration, photography, and composition. Learn to capture
          the essence of nature and translate it into visual storytelling.
        </p>
      </div>

      <!-- Card 2 -->
      <div class="bg-white/10 backdrop-blur-lg rounded-2xl p-8">
        <h3 class="text-xl font-medium text-orange-400 mb-4">
          Conscious Cooking
        </h3>
        <p class="text-white/85 leading-relaxed">
          Master techniques that honor ingredients. Focus on flavors, textures,
          and the healing properties of food.
        </p>
      </div>

    </div>
  </div>
</section>

	<!-- ===== Contacts ===== -->
	<section id="contact" class="w-full bg-neutral-50 py-24">
  <div class="max-w-6xl mx-auto px-6 space-y-24">

    <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
      
      <!-- Text -->
      <div>
        <span class="text-orange-500 uppercase tracking-wide text-sm">
          Contacts
        </span>

        <h2 class="text-3xl text-black md:text-4xl font-light mt-2 mb-6">
          Get in touch with me
        </h2>

        <div class="space-y-4 text-gray-700 leading-relaxed">
          <p>
            Whether you're looking for a <strong>private chef</strong> for an intimate gathering or want to join a <strong>creative workshop</strong>, I'd love to hear from you.
          </p>
          <p>
            Send me an email at <a href="mailto:ateliertavolaviva@gmail.com" class="text-orange-500 hover:underline">ateliertavolaviva@gmail.com</a>
          </p>

          <p>
            Text me on <a href="https://wa.me/31627208558" class="text-orange-500 hover:underline">Whatsapp</a>
          </p>

          <p>
            Join me on <a href="https://example.com" class="text-orange-500 hover:underline">AirBnB Experiences Atelier Tavola Viva</a>
          </p>
          
        </div>
      </div>

      <!-- Image -->
      <div class="w-full">
        <div class="aspect-[4/5] w-full overflow-hidden rounded-2xl shadow-lg">
          <img
            src={valuesImg}
            alt="Nature textures and organic details"
            class="w-full h-full object-cover"
          />
        </div>
      </div>
    </div>

  </div>

</section>

<!-- ===== Footer ===== -->
	<footer class="border-t border-black/30 bg-foreground text-black w-full bg-neutral-100 py-24">

    <p class="text-sm items-center justify-center text-center">
      &copy; {new Date().getFullYear()} Atelier Tavola Viva. All rights reserved.
    </p>

  </footer>
</div>
