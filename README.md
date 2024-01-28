This is the entire idea:

```css
  /** typeO works by underflowing <number>s to fake <integers>s:                                **/
  /*  --number-to-int: calc(25.4 * var(--int) / var(--int));                                     */
  /*  --n-to-interval: calc(25.4 / var(--interval) * var(--int) / var(--int) * var(--interval);  */
  --int: 4.9406564584124654e-324;
```

And the rest is details.
