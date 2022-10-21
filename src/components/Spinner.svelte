<script>
     import TailwindCss from '../TailwindCSS.svelte';
</script>
<TailwindCss/>

<div class="spinner"></div>

 <style>

  
.spinner {
    width: 7rem;
    height: 7rem;
    border-radius: 50%;
    background: conic-gradient(#171a21, #ff009e, #8700ff);
    position: relative;
    animation: spin 1.4s linear infinite;
    margin:auto;

  }
  
  .spinner::after {
    background: radial-gradient(#171a21, #171a21);
    width: 75%;
    height: 75%;
    border-radius: 50%;
    content: "";
    margin: auto;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
  }
  
  @keyframes spin {
    from {
      transform: rotate(0deg);
      
    }
  
    to {
      transform: rotate(360deg);
    }
  }
  
 </style>