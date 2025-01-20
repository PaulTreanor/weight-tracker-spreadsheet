# weight-tracker-spreadsheet
Simple Google Sheet for tracking daily weight with automatic date logging.

[Link to sheet.](https://docs.google.com/spreadsheets/d/1lI_kjZB7Dz4Ab_Z_TeYt-Y-6A8fCvCOhpQ3xBOd5jww/edit?usp=sharing)

Documenting this stuff 

## How to use this template 
1. File > Make a copy
2. Add your weight in the input cell, update it each day

You will need to personal the min and max weight range in the charts (unless you weight the same as me): 
- Click on the 3 dots in the chart
- Go to the chart "Customise" tab
- Expand "Vertical Axis" section
- Edit min and max value to be more appropriate (below and above 15kg of your current weight is a good starting point).

Historic data can be manually entered in Rows D and E. New entries automatically append through B2 input.

## Structure
- Input weight in B2
- Data stored in columns D (Date) and E (Weight)
- Helper cell G1 counts total entries
- Chart visualizes weight over time
- Helper columns H and I show last 30 days data for chart

## Formulas Explained

**Helper (G1):**
```
=COUNTA(E:E)
```

Counts filled cells in weight column to find next empty row.

**Date (D2):**
```
=IF($B$2<>"", IF(ROW()=$G$1+1, TODAY(), ""), "")
```

If weight entered in B2, adds today's date in first empty row.

**Weight (E2):**
```
=IF($B$2<>"", IF(ROW()=$G$1+1, $B$2, ""), "")
```

**Last 30 days of data (H and I)**
```
=FILTER(D:D, D:D >= TODAY()-30)
=FILTER(E:E, D:D >= TODAY()-30)
```

Copy date and weight records from D and E into rows H and I if they are younger than 30 days. 


