# Bar Race Custom Visual for Power BI
Bar Race is an implementation of the Bar Race animated chart format for Microsoft Power BI. It's a great way to show the change over time or over some other range of data in a visually engaging way.

As with all of the visuals from [Big Data Big Display](http://www.bigdatabigdisplay/), this is designed primarily for public display in common spaces, kiosks, or other automated display. However, optional play controls are provided so the visual can be used for an interactive presentation as well.

## Data Schema

The Bar Race Visual is generally designed for time series data, so a typical data set will have one row per period. Each period will have a number of categories represented by a bar, and the category has a value for that period. The category bars are animated based on the values as they change from period to period. You are not limited to a time series data set. Anything is possible as long as the "period" is ordinal and can be sorted.

A typical example is to have sales by region for each month over two years. The period is the year-month, the category is the region, and the metric is the sales.

For each period, the data set must have the following columns:

- A unique ID. This is not used in the display, but is helpful if not required to prevent Power BI from forcing the summarization of numeric fields.
- Label. This is a description of the category that will appear on the bar.
- Period Values. The period must be a expressed as a numeric value, since the data is sorted by this value. For example, a month and year can be expressed as 2020.01, 2020.02, or 202001, 202002, etc. Either format works as long as it will sort properly.
- Current Values. This is the value of the metric for the period in question. In out example, this is a numeric value for sales during this period. This must be a numeric value that can be sorted. Formatting can be controls with one of the formatting options described below. Note that percentages should be provided in decimal format and then formatted with your choice of decimal points using the formatting control.
- Prior Values. The data set must also include the value for the prior period, since this is used to define the animation from period to period. This must be a numeric value that can be sorted.
- Period Labels. This is the label for the period, in our example, it would be the year of the period for each row, e.g. 2020. The period label and sub label are displayed in the bottom right corner of the visualization so the user sees the period as it changes in the animation.
- Period Sub Labels. This is the label for the sub period, the month in our example. If a sub period is not applicable, the column may be null in which case that label is left blank in the visualization.

## Formatting Options

You can use the following formatting options to customize the look and functionality of the visual.

- Bar Label Color. Color of the text label that appears over the bars. Note that the bar colors are chosen automatically based on your chosen theme.
- Text Color. Color of the Period and Sub Period Labels.
- Font Family. Font family for all the text.
- Period Label Size. Size in pixels (px) of the Period Label
- Sub Period Label Size. Size in pixels (px) of the Sub Period Label
- Top N Rank. For each period, the categories are sorted and ranked. You may have 20 categories, but only wish to show 10. This has the effect of a category dropping off the chart if it falls out of the top 10, or vise-versa, zooming into the chart if it moves up into the top 10. This adds excitement to the visualization. In this setting you enter the value of then top n, in our example, 10. This governs the number of bars that are displayed.
- Interval (milliseconds). Time in milliseconds for each period.
- Value Format. This setting allows you to format the display of the metric value. This is a string of D3 JS formatting options. For example, .0% formats .05 as 5%.
- Show Play Controls. Toggle this option to show the play/pause control. Hiding the controls is best is an automated display situation, like a kiosk.
- Repeat Loop. Toggle this option to repeat the animation on a loop. Works best is an automated display situation, like a kiosk.

## Credits

Credit goes to the originator(s) of the bar race design. In particular, much of this implementation is based on
Joel Zief's code: https://bl.ocks.org/jrzief/70f1f8a5d066a286da3a1e699823470f
