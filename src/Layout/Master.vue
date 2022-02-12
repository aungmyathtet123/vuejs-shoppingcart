<template>
    <div>
      <Nav/>
        <slot/>  
    </div>
</template>
<script>
import Nav from "./Nav";
export default {
    components:{Nav},
    name:'Master',
}
</script>