<script>
  import Header from "./UI/Header.svelte";
  import MeetupItem from "./Meetups/MeetupItem.svelte";

  const meetups = [
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
      imageUrl:'https://static.wikia.nocookie.net/spongebob/images/2/26/Bubbletown_002.png/revision/latest/scale-to-width-down/1000?cb=20181028171458',
      address: '124 Conch St., Bikini Bottom',
      contactEmail: 'thedude@hisdudeness.com'
    }
  ]
</script>

<style>
  #meetups {
    margin-top: 5rem
  }
</style>


<Header />

<section id="meetups">  
  {#each meetups as meetup}
    <MeetupItem />
  {/each}
</section>
