<script>
  import DeviceDetector from "svelte-device-detector";
  import {Route,router,active} from 'tinro';
  import Contacts from './Contacts.svelte'; // <h1>Contacts</h1>
  import TopNav from './TopNav.svelte';

  let counter = 0;
  const addToCounter = () => {
    counter += 1;
  }


</script>


<div class="container">

  <DeviceDetector showInDevice="mobile">
    <style media="screen">
      body {
        font-size:200%;
      }
      h1 {
        font-size:2em;
        color:red;
      }
      button {
        font-size:2em;
      }
    </style>
    <p>for Mobile</p>
  </DeviceDetector>


  <nav>
  <TopNav/>
  </nav>



  <h1>Extra-Sensory Perception</h1>

  <h2
    style="font-size:10pt;
      margin-bottom:20px;
    "
    >everything you need to know about ESP</h2>


  <div id="x009" style="background:lightgray" >
    wave your friends!
  </div>




</div>


<style media="screen">
  h1, h2, h3 {
    text-align:center;
    font-family: galdeano;
    color: brown;
  }
  div.user {
    padding:3px;
    margin:3px;
  }
  .flashing {
    animation-name: flash-animation;
    animation-duration: 5s;
  }

  @keyframes flash-animation {
    0% { background: red; }
    100%   { background: blue; }
  }

	:global(.active){font-weight: bold; text-decoration: underline}
	a {outline : none}



  #app {
    display: grid;
    height: 100%;
    width: 100%;
    overflow: auto;
    grid-template:
      "nav" 3rem
      "main" 1fr
      / auto;
  }

  nav {
		z-index: 10;
    grid-area: nav;
	  color: rgb(220, 220, 220);
	  background-color:rgb(143, 159, 143);
	  font-size: 0.5rem;
	  padding: 0.25rem;
  }

 	main {
    grid-area: main;
		display: grid;
		grid-template-rows: 1;
		grid-template-columns: 1;
	}

  /* use :global since the Route element may be in another component */
	main > :global(*) {
		grid-row: 1;
		grid-column: 1;
   }


</style>


<Route path="/add-users">
  <TopNav userPermission={userPermission}/>
  <div class="templateWrap">
    <AddUsers userProfile={userProfile} userPermission={userPermission}/>
  </div>
</Route>

<Route path="/">
  landing page
</Route>




<Route path="/portfolio/*">
    <Route path="/">
        <h1>Portfolio introduction</h1>
        <nav>
            <a href="/#/portfolio/sites">Sites</a>
            <a href="/#/portfolio/photos">Photos</a>
        </nav>
    </Route>
    <Route path="/sites"><h1>Portfolio: Sites</h1></Route>
    <Route path="/photos"><h1>Portfolio: Photos</h1></Route>
</Route>
<Route path="/contacts"><Contacts /></Route>
