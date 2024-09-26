_Linear Progress = 
VAR Actual = [Gross Sales]
VAR Target = [Gross Sales Target]
VAR PERCENTAGEFILL = Actual/Target*100
RETURN
IF(HASONEVALUE(financials[Country]),
"data:image/svg+xml;utf8," & 
"<svg width='100' height='20' viewBox='-2 -2 102 22' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' display= 'block'  overflow='visible'>
  <defs>
    <linearGradient id='linear' x1='0%' y1='0%' x2='"&100+(100-PERCENTAGEFILL)&"%' y2='0%'>
      <stop offset='0%'   stop-color='navy'/>
      <stop offset='100%' stop-color='cyan'/>
    </linearGradient>
  </defs>
<rect id='track' x='0' y='3' rx='0' ry='0' width='100' height='15' fill='#D0D0D0' />
<rect id='fill' x='0' y='3' rx='0' ry='0' width="& "'"& PERCENTAGEFILL &"'"&" height='15' fill='url(#linear)'></rect>
</svg>"
, BLANK())
