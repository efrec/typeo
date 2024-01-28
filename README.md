## One stupid trick

This is the entire idea, really:

```css
  /** typeO works by underflowing <number>s to fake <integers>s:                                **/
  --int:           4.9406564584124654e-324;
  --number-to-int: calc(25.4 * var(--int) / var(--int));
  --n-to-interval: calc(25.4 / var(--interval) * var(--int) / var(--int) * var(--interval));
```

I'm using this to set everything on an exact half-baseline grid. Everything from a note's margins to its bullet points are dimensioned against a set of measurements of the body font.

## Motivation

I _bet on text_ and now I'm betting on what's next. Typographic principles ask authors to pay attention to space and rhythm in the final product because these things do, seriously, matter. Markdown asks us to focus on productivity and rarely consider _anything_ as final. It especially wants to be clear of any markup that's solely for style. Both these idioms prioritize text but do so in vastly different ways. My goal is to stop thinking about layout while writing by sticking to a really solid document design. But I made things weird from there.

I chose text baselines as the basic unit of design. This is a common, text-first approach that relies on regularly divisible blocks of text to provide reliable visual cues. Not every document meets this need, but few are harmed by missing it. Next, I wanted a much more compact layout in many cases, so the baseline unit was replaced by the half-baseline. Obsidian doesn't have a stable view width, so column units aren't as significant, but I went with a four-column layout for starters. This was plenty of annoying, fiddly work for someone still learning CSS. All this because we can't get a modulo or an abs() or a literally-anything.

## Example 1

Knowing the exact size of everything in a document allows non-vertical layouts without changing `display` settings constantly (or ever). Everything just lays out on the page. Since the document is built on baselines, you can place different elements side-by-side and see their text line up neatly, too. Nothing is ever, ever customized, and nothing ever looks sorely out of place. That's the kind of compromise I am after.

Here's a screencap of my conversion of the Classic Explorer template for RPGs into a note-level CSS class. A small amount of non-text markup was used to add the `.aside` and `.span-*` classes. It's not fully plaintext, but it's easy to ignore and keep writing.

> ![image](https://github.com/efrec/typeo/assets/103912894/f2a74a36-4035-4d8a-ae8d-b35f7f7c5816)

Text baselines align between text elements without any special placement. Even this test document looks orderly while intentionally crowding nonsense together. And like I mentioned, it achieves that result without much markup. Here's its plaintext:

> ```markdown
> | 1d4 | Conditions |
> |:---:| ---------- |
> |  1  | Concepted  |
> |  2  | Drafted    |
> |  3  | Proofread  |
> |  4  | Published  |
> { .span-1 }
> 
> | 1d4 | Conditions |
> |:---:| ---------- |
> |  1  | Concepted  |
> |  2  | Drafted    |
> |  3  | Proofread  |
> |  4  | Published  |
> { .span-1 }
> 
> | 1d4 | Conditions |
> |:---:| ---------- |
> |  1  | Concepted  |
> |  2  | Drafted    |
> |  3  | Proofread  |
> |  4  | Published  |
> { .span-1 }
> 
> | 1d4 | Conditions |
> |:---:| ---------- |
> |  1  | Concepted  |
> |  2  | Drafted    |
> |  3  | Proofread  |
> |  4  | Published  |
> { .span-1 }
> 
> After another set of four `span-1` tables, place an aside paragraph and a content paragraph.
> { .aside }
>
> This is another content paragraph. This thing's CSS is just tragic but it *does* work.
> The best systems have the worst plumbing.
> All of this is produced by an `.aside` class on the aside and a `.span-1` on each of the tables.
> Content doesn't need to be told that it's content.
> 
> ---
> 
> #### Aside and Content Tables
> 
> Asides and content are *not* on the four-column grid, which makes this whole exercise a bit futile, really.
> Originally of course, they were, but I wanted more pragmatic constraints on line lengths.
> When those constraints are better satisfied, I might snap everything back to the vertical grid.
> Filed under "todo".
> 
> This is a test of an aside and a content-width table. Boy-howdy, sure is.
> Text should align between tables and text.
> { .aside }
> 
> | 1d4 | Layout Project                                                |
> |:---:| ------------------------------------------------------------- |
> |  1  | **Manuscript layout.** *Clean, approachable, and timeless.*   |
> |  2  | **Column layout.** *Robust, functional, and familiar.*        |
> |  3  | **Modular layout.** *Dense, orderly, and experimental.*       |
> |  4  | **Hierarchical layout.** *Intuitive, engaging, and exciting.* |
> 
> Even when using `content` tables, text is right up against the table.
> Maybe this is just right, but often it is too close.
> To add spacing around a table, you can add a line break (`<br>`).
> Each `br` tag adds only a half-grid row of height, not a full one, to give you a greater degree
> of control over layout.
> 
> Spacing around a table could be controlled by table classes, e.g. "space-tight" and "space-loose",
> instead of using elements-as-layout (*boo*).
> ```

## Example 2

Normal documents don't have any layout at all. They need to look like something, but not like anything special. Here's some notes on generating means. It's readable, and looks fine, if you ignore the default theme.

> ![image](https://github.com/efrec/typeo/assets/103912894/d6949d33-4b68-4fb3-a482-93abe7e8fa6b)
