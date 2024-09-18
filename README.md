# Svelte Customizable Quill Editor

An easy to use and flexible Quill editor for Svelte

## Authors

-   [@Hai567](https://github.com/Hai567)

## Installation

Install with npm

```bash
  npm i quill @canadies/svelte-customizable-quill
```

## Basic Usage/Examples

```javascript
<script>
    import QuillEditor from "@canadies/svelte-customizable-quill"
    import { onMount } from "svelte"
    let data = "asdfasdf"
    let Quill
    let quillOptions = {
        theme: "snow",
    }
    let quillReady = false

    const typingEvent = (event) => {
        const { text, html } = event?.detail ?? {}
        data = html
    }

    onMount(async () => {
        const quillModule = await import("quill")
        Quill = quillModule.default
        quillReady = true // Set the flag when Quill is ready
    })
</script>

<svelte:head>
    <link
        rel="stylesheet"
        href="https://unpkg.com/quill@2.0.2/dist/quill.snow.css"
        crossorigin
    />
</svelte:head>

{#if quillReady}
    <h1>Hello</h1>
    <QuillEditor
        {Quill}
        options={quillOptions}
        {data}
        on:typing={typingEvent}
    />
{/if}

```
