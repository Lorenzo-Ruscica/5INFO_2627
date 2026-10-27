<script>
	let { title } = $props();
  </script>
  
  <button class="btn">
	<span>{title}</span>
	<span>▼</span>
  </button>
<style>
	.btn {
	  display: flex;
	  justify-content: space-between;
	  background: red;
	  color: white;
	  border: none;
	  padding: 15px 25px;
	  border-radius: 15px;
	  width: 320px;
	  font-size: 20px;
	  margin-bottom: 25px;
	}
  </style>
  