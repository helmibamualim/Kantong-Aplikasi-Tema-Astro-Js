# 🎨 Final Polish Quick Reference

## Animation Timing Standards

### Interactions (User-Triggered)
```
Duration: 500ms
Easing: ease-in-out
Properties: transform, opacity, colors
```

### Ambient (Auto-Running)
```
Duration: 4-8s
Easing: ease-in-out / linear
Properties: background-position, transform
```

---

## Spacing Standards

### Gaps
- Small: `gap-3` (12px)
- Medium: `gap-4` (16px)
- Large: `gap-5` (20px)

### Padding
- Cards: `p-8` (32px)
- Buttons: `px-12 py-5` (48px x 20px)
- Pills: `px-6 py-3.5` (24px x 14px)

### Margins
- Small: `mb-4` (16px)
- Medium: `mb-6` (24px)
- Large: `mb-12` (48px)

---

## Border Radius Standards

```
Cards: rounded-3xl (24px)
Buttons: rounded-xl (12px)
Pills: rounded-full
Icons: rounded-lg (8px)
```

---

## Shadow Standards

### Hover States
```css
hover:shadow-2xl
hover:shadow-[0_0_30px_rgba(251,146,60,0.3)]
```

### Focus States
```css
focus:ring-4
focus:ring-primary-500/20
focus:shadow-[0_0_20px_rgba(251,146,60,0.2)]
```

---

## Scale Standards

### Subtle (Preferred)
```
hover:scale-[1.02] - Trust badges
hover:scale-[1.03] - Category cards
hover:scale-105 - Buttons, small elements
```

### Prominent
```
hover:scale-110 - Icons, micro-interactions
```

---

## Color Opacity Standards

### Backgrounds
```
Glassmorphism: bg-white/85 dark:bg-dark-900/85
Overlays: bg-white/10, bg-black/60
Borders: border-white/20, border-white/30
```

### Effects
```
Glow: opacity-20 to opacity-30
Grain: opacity-[0.012]
Blueprint: opacity-[0.03]
```

---

## Gradient Standards

### 2-Layer (Categories)
```
from-slate-400 via-gray-400 to-slate-500
```

### 3-Layer (Features)
```
from-blue-500 via-blue-400 to-cyan-500
```

### Radial (Hero)
```
from-primary-400/15 via-primary-500/5 to-transparent
```

---

## Animation Classes

### Custom Animations
```css
.animate-pulse-slow - 6s gentle pulse
.animate-float-slow - 4s floating motion
.animate-grain - 8s texture movement
.animate-shimmer - 3s gradient slide
```

### Timing
```css
duration-500 - Interactions
duration-700 - Image zoom
duration-1000 - Shine effects
```

---

## Hover Patterns

### Cards
```astro
hover:shadow-2xl
hover:-translate-y-1.5
hover:scale-[1.03]
transition-all duration-500 ease-in-out
```

### Links
```astro
<span class="relative">
  Text
  <span class="absolute bottom-0 left-0 w-0 h-0.5 
    bg-primary-600 group-hover:w-full 
    transition-all duration-500 ease-in-out">
  </span>
</span>
```

### Icons
```astro
group-hover:scale-110
group-hover:text-primary-600
transition-all duration-500 ease-in-out
```

---

## Focus States

### Input Fields
```astro
focus:border-primary-500
focus:ring-4
focus:ring-primary-500/20
focus:shadow-[0_0_20px_rgba(251,146,60,0.2)]
transition-all duration-500 ease-in-out
```

### Buttons
```astro
focus:outline-none
focus:ring-4
focus:ring-primary-500/20
```

---

## Staggered Animation Pattern

```astro
{items.map((item, i) => (
  <div style={`animation: fadeInUp 0.6s ease-in-out ${i * 0.15}s both;`}>
    {item}
  </div>
))}
```

Delays: 0s, 0.15s, 0.3s, 0.45s, 0.6s...

---

## Glow Effect Pattern

```astro
<!-- Element -->
<div class="relative group">
  Content
  
  <!-- Glow -->
  <div class="absolute -inset-1 bg-gradient-to-r from-primary-600 to-primary-700 
    rounded-3xl blur-xl opacity-0 group-hover:opacity-20 
    transition-opacity duration-500 ease-in-out -z-10">
  </div>
</div>
```

---

## Multi-Layer Background Pattern

```astro
<section class="relative">
  <!-- Layer 1: Base -->
  <div class="absolute inset-0 bg-gradient-to-br from-dark-950 via-primary-950 to-dark-950"></div>
  
  <!-- Layer 2: Pattern -->
  <div class="absolute inset-0 opacity-[0.03]">
    <svg>...</svg>
  </div>
  
  <!-- Layer 3: Texture -->
  <div class="absolute inset-0 opacity-[0.012] mix-blend-overlay animate-grain">
    <svg>...</svg>
  </div>
  
  <!-- Layer 4: Spotlight -->
  <div class="absolute ... animate-pulse-slow"></div>
  
  <!-- Layer 5: Vignette -->
  <div class="absolute inset-0 bg-gradient-to-b from-dark-950/40 via-transparent to-dark-950/60"></div>
  
  <!-- Content -->
  <div class="relative z-10">
    Content here
  </div>
</section>
```

---

## Micro-Interaction Pattern

```astro
<!-- Badge with Scale -->
<span class="... group-hover:scale-110 transition-all duration-500 ease-in-out">
  0
</span>

<!-- Icon with Color Change -->
<svg class="... group-hover:scale-110 group-hover:text-primary-600 
  transition-all duration-500 ease-in-out">
  ...
</svg>
```

---

## Glassmorphism Pattern

```astro
<div class="bg-white/85 dark:bg-dark-900/85 
  backdrop-blur-xl 
  border border-gray-200/50 dark:border-dark-800/50">
  Content
</div>
```

---

## Success Feedback Pattern

```javascript
// Show success state
target.classList.add('!bg-green-600', '!from-green-600', '!to-green-700');
icon.classList.add('animate-bounce');

// Reset after 2 seconds
setTimeout(() => {
  target.classList.remove('!bg-green-600', '!from-green-600', '!to-green-700');
  icon.classList.remove('animate-bounce');
}, 2000);
```

---

## Performance Best Practices

### DO ✅
- Use `transform` over `position` changes
- Use `opacity` over `visibility`
- Use CSS animations over JavaScript
- Add `will-change` for complex animations
- Use `ease-in-out` for natural feel

### DON'T ❌
- Animate `width`, `height`, `top`, `left`
- Use aggressive durations (< 200ms)
- Stack too many animations
- Forget to remove `will-change` after animation
- Use `ease` or `linear` for interactions

---

## Testing Checklist

### Visual
- [ ] All animations smooth at 60fps
- [ ] No layout shifts (CLS = 0)
- [ ] Consistent spacing throughout
- [ ] Proper z-index layering

### Interaction
- [ ] Hover states immediate
- [ ] Focus states visible
- [ ] Click feedback clear
- [ ] Keyboard navigation works

### Performance
- [ ] No janky animations
- [ ] Fast initial load
- [ ] Smooth scrolling
- [ ] No memory leaks

---

**Quick Reference Version**: 1.0  
**Last Updated**: 10 Februari 2026  
**For**: BuildMart Flagship Theme
