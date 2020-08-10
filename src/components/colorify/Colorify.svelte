
<DraggableDiv>
    <div class="themes">
    <button on:click={randomColors}>Colorify</button>
    {#each variables as variable, i}
        <label>
            <input type=checkbox bind:group={varcheck} value={variable}> {variable}
            <input style="background-color: {color[i]}" bind:value={color[i]}
                   on:keydown={updateValue(color[i], variable)}>
        </label>
    {/each}
    </div>
</DraggableDiv>

<script>
    import DraggableDiv from './DraggableDiv.svelte'
    import {onMount} from 'svelte';

    let color = new Array(100).fill("")
    export let variables = []
    const rand = () => Math.floor(Math.random() * 255)
    let varcheck = []

    function randomColors() {
        for (const [i, value] of variables.entries()) {
            if (varcheck.includes(value)) {
                let [a1, a2, a3] = [rand(), rand(), rand()]
                document.body.style.setProperty(variables[i], `rgb(${a1}, ${a2}, ${a3})`);
                [color[i]] = [`rgb(${a1}, ${a2}, ${a3})`]
            }
        }
    }

    function getInitialValues() {
        for (const [i, value] of variables.entries()) {
            let entry = getComputedStyle(document.body).getPropertyValue(value)
            color[i] = entry
        }
    }

    const updateValue = (value, selector) => document.body.style.setProperty(selector, value);

    function getAllCSSVariableNames() {
        const cssVars = Array.from(document.styleSheets)
                .filter(
                        sheet =>
                                sheet.href === null || sheet.href.startsWith(window.location.origin)
                )
                .reduce(
                        (acc, sheet) =>
                                (acc = [
                                    ...acc,
                                    ...Array.from(sheet.cssRules).reduce(
                                            (def, rule) =>
                                                    (def =
                                                            rule.selectorText === ":root"
                                                                    ? [
                                                                        ...def,
                                                                        ...Array.from(rule.style).filter(name =>
                                                                                name.startsWith("--")
                                                                        )
                                                                    ]
                                                                    : def),
                                            []
                                    )
                                ]),
                        []
                );
        return cssVars
    }

    const isColor = (strColor) => {
        const s = new Option().style;
        s.color = strColor;
        return s.color !== '';
    }

    onMount(() => {
        let allCssVars = getAllCSSVariableNames()
        variables = allCssVars.filter(cssvar => {
            if (!isColor(getComputedStyle(document.body).getPropertyValue(cssvar).toLowerCase()) == '') {
                return true
            }
        });
        varcheck = variables
        getInitialValues()
    });
</script>


<style>
    .themes {
    }

    input {
        width: 100%;
        color: black;
    }

    input[type='checkbox'] {
        width: 20px;
    }

    button {
        width: 100%
    }
</style>



