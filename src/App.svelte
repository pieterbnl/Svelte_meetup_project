<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";

  let title = '';
  let subtitle = '';
  let address = '';
  let email = '';
  let description = '';
  let imageUrl = '';

  let meetups = [
    {
      id: 'm1',
      title: 'Coding Bootcamp',
      subtitle: 'Learn to code in under 2 years',
      description: 'In this meetup we will have some supposedly experts to teach you stuff you never knew you needed to know',
      imageUrl: 'https://media.istockphoto.com/photos/smiling-confident-indian-coder-picture-id1282402777?s=612x612',
      address:'Keizer Karel V Singel 45, Eindhoven',
      contactEmail: 'thedude@hisdudeness.com'
    },
    {
      id: 'm2',
      title: 'Sing along',
      subtitle: 'Let\'s sing together',
      description: 'We will sing for world peace',
      imageUrl:'https://i.pinimg.com/564x/8c/82/84/8c8284bd9ff5c81c9478a8f72cb42662.jpg',
      address: '124 Conch St., Bikini Bottom',
      contactEmail: 'thedude@hisdudeness.com'
    }
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      imageUrl: imageUrl,
      contactEmail: email,
      address: address
    };

    meetups = [...meetups, newMeetup];
  }
</script>

<style>
  main {
    margin-top: 5rem
  }
</style>

<Header />

<main>
  <!-- <MeetupGrid meetups={meetups}/> -->
  <!-- using preventDefault so that no http requests get send
  as all can handled on the client side -->
  <form on:submit|preventDefault="{addMeetup}">
    <div class="form-control">
      <label for="title">Title</label>
      <input type="text" id="title" bind:value={title} />
    </div>
    <div class="form-control">
      <label for="subtitle">Subtitle</label>
      <input type="text" id="subtitle" bind:value={subtitle} />
    </div>
    <div class="form-control">
      <label for="address">Address</label>
      <input type="text" id="address" bind:value={address} />
    </div>
    <div class="form-control">
      <label for="imageUrl">Image Url</label>
      <input type="text" id="imageUrl" bind:value={imageUrl} />
    </div>
    <div class="form-control">
      <label for="email">E-mail</label>
      <input type="text" id="email" bind:value={email} />
    </div>
    <div class="form-control">
      <label for="description">Description</label>
      <textarea rows="3" id="description" bind:value={description} />
    </div>
    <button type="submit">Save</button>   
    
  </form>
  <MeetupGrid {meetups}/>  
</main>