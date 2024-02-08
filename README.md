## One stupid trick

This is the entire idea:

```css
  /** This works by underflowing <number>s to fake <integers>s: **/
  --int:           4.9406564584124654e-324;
  --number-to-int: calc(25.4 * var(--int) / var(--int));
  --n-to-interval: calc(
      25.4 / var(--interval)
      * var(--int) / var(--int)
      * var(--interval));
```

I use this hacky trick to set everything on a half-baseline grid that's precise to the pixel. To proportion that grid, I take a set of measurements of the body font, then use a simple set of math-y rules to set every other element on the page in proportion to the text.

The method doesn't work across all browsers on all platforms, and we have no reason to believe it will work long into the future on any given one, either. So it's a trick, and a stupid trick, and the fact it works is a product of a particular environment. Let's just appreciate these things for what they are: toys.

## Motivation

Typographic principles ask authors to pay attention to space and rhythm (because these things matter). Markdown asks us to focus on productivity (to the exclusion of all else). To keep it readable as plaintext, it excludes most markup for style and layout. These two ideas are locked in debate over what makes text meaningful. My goal is to get a solid layout no matter what I write through absurdly sturdy document design.

I chose text baselines as the rows of a grid layout. This is a common approach that produces orderly blocks of text to provide reliable visual cues. Not every document meets this need, but few are harmed by missing it. This produced a set of documents that sprawled vertically, so the baseline unit was replaced by the half-baseline. Notes in Obsidian have a variable view width, so grid columns aren't significant (as in "meaningful"), but I adopted the twelve-column layout. This became the grid system, from which came the need to "fit to the grid".

## Work in progress

I uploaded this to shame myself into finishing this project that's been halfway to half-done for a year, now, and plaguing my Obsidian vault in the meantime. That basically worked—this CSS is usable (enough) to transplant into other vaults. This is one of four separate typography projects I am working on, so progress here will be slow.

My motivation is to remain a productive writer, so to get new vault styles I swap between Themes (instead of updating this CSS constantly). That will slow down the pace of fixes, updates, etc. on this concept. Hopefully, we get some sort of trigonometry support or even just `abs()` so I can do more fun stuff, and that will shift my focus back to doing math-y layout in pure CSS. Until then.
