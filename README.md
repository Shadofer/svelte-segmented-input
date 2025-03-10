# svelte-segmented-input

A simple component for number-only segmented input. Ideal for phone numbers or 2FA codes

## HOW TO USE:

```
<script>
    import SvelteSegmentedInput from 'svelte-segmented-input'

    let code
</script>

<SvelteSegmentedInput bind:value="{code}" length="{6}" style="{{borderColor: 'black'}}" />
```

`value` is the current value of the input as a string or the string 'typing' if not every field is populated

`length` is the number of fields. accepts number or an array of numbers. when an array is passed, it will create the segments such as for an array [3, 3, 4] the input will look like this: [] [] [] - [] [] [] - [] [] [] []

`style` is an object which holds css properties and their value. Possible css properties to change: (property: corresponding var, default value)

### input

-   font-size: var(--fontSize, 2rem);
-   border-radius: var(--borderRadius, 0.4rem);
-   border: var(--borderWidth, 2px) solid var(--borderColor, #e5e5e5);
-   padding: var(--padding, 0.25rem 1rem);
-   background-color: var(--bgInput, transparent);

### input:focus

-   border: var(--borderWidth, 2px) solid var(--borderColorActive, #5f91f0);

### input-wrapper

-   width: var(--inputWidth, 100%);
-   background-color: var(--bgWrapper, transparent);

Alternatively, you can target each item with a descendant selector, as all elements are inside a section with id #input-wrapper

## Known issues

1. This solution isn't accessible, as it relies on multiple input elements and breaks a lot of browsers behaviours (i. e. ctrl+f to search)
2. On mobile phones it is possible to input + and - characters. I have no idea how it happens
3. Binding the length property will break when length is smaller than the number of fields that are populated. Please, don't bind the length property
4. value property is not currently a 2-way binding, it shold be used as a read-only property for now
