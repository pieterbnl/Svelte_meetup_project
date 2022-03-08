<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";

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

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />

<main>
  <!-- <MeetupGrid meetups={meetups}/> -->
  <!-- using preventDefault so that no http requests get send
  as all can handled on the client side -->
  <form on:submit|preventDefault="{addMeetup}"> 
  <TextInput 
    id="title"
    label="Title"
    type="text"
    value={title} 
    on:input={(event) => title = event.target.value} />
<TextInput 
    id="subtitle"
    label="Subtitle"
    type="text"
    value={subtitle} 
    on:input={(event) => subtitle = event.target.value} />
<TextInput 
    id="address"
    label="Address"
    type="text"
    value={address} 
    on:input={(event) => address = event.target.value} />
<TextInput 
    id="imageUrl"
    label="Image Url"
    type="text"
    value={imageUrl} 
    on:input={(event) => imageUrl = event.target.value} />
<TextInput 
    id="email"
    label="E-mail"
    type="email"
    value={email}     
    on:input={(event) => email = event.target.value} />
<TextInput 
    id="description"
    label="Description"
    type="textarea"
    value={description} 
    on:input={(event) => description = event.target.value} />

    <Button type="submit" caption="Save" />   
    
  </form>
  <MeetupGrid {meetups}/>  
</main>