<script>

  import { onMount } from 'svelte';
  
  let data = false
  let loading = false;
  let error = false;
  
  let url = "";
  let id = false;
  let embedCode = false;
  
  function getId(){
    
    // "https://www.youtube.com/watch?v=cr0tASqUF64"
    if(url !== ""){
      var regExp = /^.*(youtu\.be\/|v\/|u\/\w\/|embed\/|watch\?v=|\&v=)([^#\&\?]*).*/;
      var match = url.match(regExp);
      if (match && match[2].length == 11) {
        id = match[2];
        
        embedCode = `<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/${id}" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>`;
        
      } else {
        //error
      }
    }

    
  }
  
</script>


<a href="https://www.cinetools.net"
  ><img
    src="./img/tubetools.png"
    id="logo"
/></a>
<div class="wrap">
  <main id="main">
    <div class="wdgt wdgt-main">
      <div class="wdgt-content p-3">
        
        
        <div class="info">
          
          Get the thumbnail and embed code of any YouTube video.
          
        </div>
        
     
    <label>YouTube video URL</label>    
  <input type="text" class="form-control mb-0" bind:value={url} on:keyup={getId}>
  
 
  
  {#if id}
  
  <label>Thumbnail</label>
  <img src="https://img.youtube.com/vi/{id}/maxresdefault.jpg" class="img-fluid" />
  
  <label>Embed Code</label>
  <textarea class="form-control">{embedCode}</textarea>

  {/if}
 


      </div>
    </div>
  </main>
</div>