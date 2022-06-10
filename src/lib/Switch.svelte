<script>
  import * as styleManager from './styleManager';

  export let key;
  export let checked = false;
  
  $: value = checked ? '#252525' : '#ffffff'; 
	
  $: styleManager.set(key, value);
</script>

<style>
  .switch {
    position: absolute;
    top: 1%;
    right: 0.7%;
    display: inline-block;
    width: 60px;
    height: 30px;
  }

  .switch input {
    opacity: 0;
    width: 0;
    height: 0;
  }

  .slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 4px;
    bottom: 0;
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 34px;
    box-shadow: 0 0 3px #000000;
  }

  .slider:before {
    position: absolute;
    content: "";
    height: 22px;
    width: 22px;
    left: 4px;
    bottom: 4px;
    background-color: #ffffff;
    box-shadow: 0 0 3px #000000;
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 50%;
  }

  input:checked + .slider {
    background-color: #505050;
    box-shadow: 0 0 3px #000000;
  }

  input:checked + .slider:before {
    -webkit-transform: translateX(26px);
    -ms-transform: translateX(26px);
    transform: translateX(26px);
  }
</style>


<label class="switch">
  <input type="checkbox" bind:checked />
  <span class="slider" />
</label>