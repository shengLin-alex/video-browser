<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>

<script type="text/javascript">

    import SearchBar from './components/SearchBar';

    export default {
        name: 'App',
        components: {
            SearchBar
        },
        methods: {
            onTermChange(searchTerm) {
                console.log(searchTerm);
            }
        }
    };

</script>