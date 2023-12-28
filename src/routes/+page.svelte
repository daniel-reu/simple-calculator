<script lang="ts">
    import {evaluate} from "mathjs";
    import Button from "../components/Button.svelte" 

    const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
    const symbols = ["/", "*", "-", "+", "."];

    let inputElement: string = "";

    function calculate() {
        inputElement = String(evaluate(inputElement));
    }

    function addToDisplay(value: string) {
        if(!inputElement && symbols.includes(value)) return;
        if(inputElement &&
            symbols.includes(inputElement.split("")[inputElement.length - 1]) &&
             symbols.includes(value)
        ) return;
        inputElement += value;
    }

</script>

<div class="flex flex-col justify-center w-full items-center min-h-screen">
    <!-- Calculator frame -->
    <div class="rounded-md border-2 border-solid border-slate-800 border-spacing-5 bg-gray-600 text-white">
        <!-- Title bar -->
        <div class="flex flex-row ms-2 mt-2 me-2 mb-5">
            <!-- Title -->
            <div class="pe-[150px] select-none">Calculator</div>
            <!-- Minimize, Maximize and Close Button -->
            <div class="flex gap-4">
                <span class="cursor-default">&#128469;</span>
                <span class="cursor-default">&#x1F5D6;</span>
                <span class="cursor-default">&#x2715;</span>
            </div> 
        </div>
        
        <!-- Input field -->
        <div class="ms-2 mt-2 me-2 mb-5 p-4">
            <input type="text" bind:value="{inputElement}" class="w-full bg-gray-600 text-right outline-none cursor-default" readonly>
        </div>

        <div class="grid grid-cols-4 gap-3 m-2">
            <Button onClick="{addToDisplay}" value="{"+"}" variation="action"/>
            <Button onClick="{addToDisplay}" value="{"7"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"8"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"9"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"-"}" variation="action"/>
            <Button onClick="{addToDisplay}" value="{"4"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"5"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"6"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"*"}" variation="action"/>
            <Button onClick="{addToDisplay}" value="{"1"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"2"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"3"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"/"}" variation="action"/>
            <Button onClick="{addToDisplay}" value="{"0"}" variation="default"/>
            <Button onClick="{addToDisplay}" value="{"."}" variation="default"/>
            <Button onClick="{calculate}" value="{"="}" variation="default"/>
            <Button onClick={() => inputElement = ""} variation="action">C</Button>
        </div>
    </div>
</div>

<style lang="postcss">
    :global(html) {
        background-color: #8697d1;
        font-family: Arial, Helvetica, sans-serif;
    }
</style>