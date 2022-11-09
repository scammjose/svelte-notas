<script>

    export let title;
    export let text;
    export let color;
    export let id;

    import {createEventDispatcher} from 'svelte';
    import {darkmode} from '../store/store';

    const dispatch=createEventDispatcher();

    function handleChange(){
        dispatch('update',{
            id:id,
            text:text,
            color:color,
            title:title
        });
    }

    function handleColor(){
        dispatch('color',{
            id:id
        });
    }

    function handleRemove(){
        dispatch('remove',{
            id:id
        });
    }

</script>

<div class={$darkmode ? 'Note-darkmode' : 'Note'}>
    <div class="Note-container" style={$darkmode ? 'background-color:#232531' : 'background-color:'+color}>
        <div class="header" style={$darkmode ? 'background-color:'+color : ''}>
            <div class="options">
                <button on:click={handleColor}><svg xmlns="http://www.w3.org/2000/svg" height="40" width="40"><path d="M20 36.375q-3.375 0-6.354-1.292-2.979-1.291-5.208-3.521-2.23-2.229-3.521-5.208Q3.625 23.375 3.625 20q0-3.458 1.313-6.458 1.312-3 3.583-5.209 2.271-2.208 5.312-3.458 3.042-1.25 6.5-1.25 3.292 0 6.188 1.104t5.083 3.042q2.188 1.937 3.479 4.604 1.292 2.667 1.292 5.792 0 4.5-2.646 7.041-2.646 2.542-6.854 2.542h-3.083q-.667 0-1.104.479-.438.479-.438 1.063 0 .958.604 1.854.604.896.604 1.979 0 1.542-.875 2.396-.875.854-2.583.854ZM20 20Zm-9.458 1.208q.916 0 1.541-.625.625-.625.625-1.541 0-.875-.625-1.5t-1.541-.625q-.875 0-1.5.625t-.625 1.5q0 .916.625 1.541.625.625 1.5.625Zm5.166-6.916q.875 0 1.5-.625t.625-1.5q0-.875-.625-1.5t-1.5-.625q-.916 0-1.541.625-.625.625-.625 1.5t.625 1.5q.625.625 1.541.625Zm8.625 0q.875 0 1.5-.625t.625-1.5q0-.875-.625-1.5t-1.5-.625q-.875 0-1.5.625t-.625 1.5q0 .875.625 1.5t1.5.625Zm5.25 6.916q.875 0 1.5-.625t.625-1.541q0-.875-.625-1.5t-1.5-.625q-.875 0-1.5.625t-.625 1.5q0 .916.625 1.541.625.625 1.5.625ZM20 33.75q.417 0 .625-.188.208-.187.208-.604 0-.583-.604-1.187-.604-.604-.604-2.229 0-1.834 1.229-3.125 1.229-1.292 3.063-1.292h2.958q3 0 4.937-1.771 1.938-1.771 1.938-5.187 0-5.292-4.021-8.605-4.021-3.312-9.354-3.312-5.917 0-10.021 4-4.104 4-4.104 9.75 0 5.708 4.021 9.729Q14.292 33.75 20 33.75Z"/></svg></button>
                <button on:click={handleRemove}><svg xmlns="http://www.w3.org/2000/svg" height="40" width="40"><path d="M11.208 34.708q-1.083 0-1.854-.77-.771-.771-.771-1.855V9.25H6.917V6.625h7.791V5.292h10.584v1.333h7.833V9.25h-1.667v22.833q0 1.084-.791 1.855-.792.77-1.875.77ZM28.792 9.25H11.208v22.833h17.584ZM15.333 28.625h2.625V12.667h-2.625Zm6.709 0h2.666V12.667h-2.666ZM11.208 9.25v22.833Z"/></svg></button>
            </div>
        </div>

        <div class="content">
            <div class="title">
                <input type="text" placeholder="Sin titulo..." bind:value={title} on:change={handleChange}>
            </div>
            <div class="text">
                <textarea cols="30" rows="10" placeholder="Escribir..." bind:value={text} on:change={handleChange}></textarea>
            </div>
        </div>
    </div>
</div>

<style>

    .Note{
        background-color: white;
        border-radius: 3px;
        border:solid 2px transparent;
        overflow: hidden;
        height: 400px;
    }

    .Note-darkmode{
        background-color: #232531;
        border-radius: 3px;
        border: solid 2px transparent;
        height: 400px;
        overflow: hidden;
    }

    .Note-container{
        height: 100%;
    }

    .Note:focus-within{
        border:solid 2px #000;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    }

    .Note-darkmode:focus-within{
        border:solid 2px cyan;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    }

    .Note .Note-container .header, .Note-darkmode .Note-container .header{
        padding: 5px;
    }

    .header .options{
        display: flex;
        justify-content: space-between;
    }

    .Note .content, .Note-darkmode .content{
        padding: 0 20px;
    }

    .text textarea{
        width: 100%;
        border: 0;
        outline: none;
        resize: none;
        height: 250px;
    }

    .title input{
        font-size: 22px;
        font-weight: bold;
        padding: 10px 0;
        outline: none;
        border: none;
        width: 100%;
    }

    button{
        margin: 0;
        border: none;
        background-color: transparent;
        cursor: pointer;
    }

    textarea, input{
        background: transparent;
    }

    button svg{
        fill: rgba(0, 0, 0, 0.3);
    }

    button:hover svg{
        fill: black;
    }


</style>