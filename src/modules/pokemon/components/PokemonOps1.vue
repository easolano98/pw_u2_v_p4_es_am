<template>
<div class="contenedor-opciones">
 <ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
  </ul>
</div>
 
</template>

<script>
export default {};
</script>

<style scope>
ul{
  list-style-type: none;
}

li{
  border:1px solid black;
  border-radius: 5px;
  background-color: white;
  margin-bottom: 10px;
  width: 200px;
  cursor: pointer;
}

li:hover{
  background-color: black;
  color: white;
  border: 1px inset white;
}
.contenedor-opciones{
  display: flex;
  justify-content: center;
}

</style>