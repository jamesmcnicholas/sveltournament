<script>
	/**
	 * @type {Boolean}
	 */
	 export var menuOpen;
</script>

<style>	
/* Dropdown Button */
.dropbtn {
  background-color: #81B29A;
  color: white;
  padding: 16px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 15px;
  width: 10rem;
  margin-left: 1rem;
}
	
	/* Dropdown button on hover & focus */
.dropbtn:hover, .dropbtn:focus {
  background-color: #96c2ad;
  border-radius: 15px;
}

</style>

  <button on:click class="dropbtn">{!menuOpen ? "+ Add Partner" : "Cancel"}</button>
