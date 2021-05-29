<template>
    <div>
        <select  v-on:change="selectTopic($event)" class="form-select mb-3" aria-label="Default select example">
            <option selected disabled>Please choose your favorite topic</option>
            <option value="java">java</option>
            <option value="css">css</option>
            <option value="git">git</option>
            <option value="rails">rails</option>
            <option value="sql">sql</option>
            <option value="angularjs">angularjs</option>
            <option value="php">php</option>
            <option value="iOS">iOS</option>
            <option value="android">android</option>
            <option value="java">java</option>
            <option value="c#">c#</option>
            <option value="game development">game development</option>
            <option value="databases">databases</option>
            <option value="wordpress">wordpress</option>
            <option value="html">html</option>
            <option value="ruby">ruby</option>
            <option value="App Development">App Development</option>
            <option value="computer science">computer science</option>
            <option value="aws">aws</option>
            <option value="cloud security">cloud security</option>
            <option value="bug">bug</option>
            <option value="iot">iot</option>
            <option value="smalltalk">smalltalk</option>
            <option value="misc">misc</option>
            <option value="Go">Go</option>
            <option value="security">security</option>
            <option value="ctf">ctf</option>
            <option value="learn to code">learn to code</option>
            <option value="javascript">javascript</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'Dropdown',
    methods: {
        selectTopic: function(value) {
            // alert(event.target.value);
            this.$emit('update:option', value);
        }
    }
}
</script>


