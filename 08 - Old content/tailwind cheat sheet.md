
### How to create a heading with gradient backgroud

- we use both `text-transparent` and `bg-clip-text` propreties

```javascript
<p className="upercase font-semibold tracking-widest bg-gradient-to-r from-slate-500 to-slate-950 text-transparent bg-clip-text">Real-world Results</p>
```


### How to set custom utility classes 

```css

@layer base {
    .hero__ring {
        @apply rounded-full absolute inset-0 top-1/2 left-1/2 -translate-x-1/2 md:translate-x-[-48%] lg:translate-x-[-51%] 
        -translate-y-1/2 border-2 border-gray-300/5 shadow-[0_0_80px_inset] shadow-gray-500/5 
    }
}

@layer utilities {
    .container {
        @apply lg:mx-20
    }
}
```