<script type="text/javascript">

  const users =[
    {name:'Alice'},
    {name:'Bob'},
    {name:'Charlie'},
    {name:'Dominique'},
    {name:'Emile'},
    {name:'Peter'},
    {name:'Rod'},
    {name:'Simone'},
    {name:'Tania'},
  ];


  function click_friend() {
    const b = this;
    console.log({b})
    console.log(`name:${this.name}`)
    //$('#id').addClass('flash');
    const list = document.getElementById('x009').classList;
    list.add('flashing')
    setTimeout(function() {
           //$('#id').removeClass('flash');
           list.remove('flashing')
     }, 5000);
  }
  
</script>


// ===========================================================================

<div style="text-align:center; margin:0 auto;">

{#each users as user}
  <div class="user">
    <button
        type="button"
        name="{user.name}"
        on:click={click_friend}
        >{user.name}</button>
  </div>
{/each}

</div>
