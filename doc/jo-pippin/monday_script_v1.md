# Summary 
Locates Mondays and extend through Tuesday. Shows Opening range and warning when Monday H/L is breached on Tuesday 

## Indicator overview
* Locates Mondays and extend through Tuesday. 
* Shows Opening range and warning when Monday H/L is breached on Tuesday 

![description](./assets/monday_script_v1/description.png?raw=true)

## Updates

### Update 1

added option to extend monday opening range to the end of the week

![update1](doc/jo-pippin/assets/monday_script_v1/update_01.png)

### Update 2

![update2](doc/jo-pippin/assets/monday_script_v1/update_02.png)

### Update 3

![update3](doc/jo-pippin/assets/monday_script_v1/update_03.png)

## Code Snippets 

```pine

//Jo-Pippin 
//@version=5
indicator(title='Mondays | Opens V1', shorttitle='Mondays | Opens V1', overlay=true , max_bars_back = 500)

IB_DURATION    = input.string("5M", options = ["5M", "10M", "30M"], title = "IB DURATION", group = "Monday Settings")
IB_D           = IB_DURATION == "5 Min" ? '0000-0005:2' : IB_DURATION == "10M" ? '0000-0010:2' : IB_DURATION == "30M" ? '0000-0030:2' : '0000-0005:2'

sunday_bar     = ta.barssince(dayofweek == dayofweek.sunday)
monday_bar     = ta.barssince(dayofweek == dayofweek.monday)
tuesday_bar    = ta.barssince(dayofweek == dayofweek.tuesday)
wednesday_bar  = ta.barssince(dayofweek == dayofweek.wednesday)
thursday_bar   = ta.barssince(dayofweek == dayofweek.thursday)
friday_bar     = ta.barssince(dayofweek == dayofweek.friday)
saturday_bar   = ta.barssince(dayofweek == dayofweek.saturday)

inp_text_size         = input.string("Tiny", options = ["Tiny", "Small","Normal"], title = "Text Sizs", group = "Monday Settings")
TextSize              = inp_text_size == "Tiny" ? size.tiny : inp_text_size == "Small" ? size.small : inp_text_size == "Normal" ? size.normal : na
inp_line_style        = input.string("Dotted", options = ["Dotted", "Solid", "Dashed"], title = "Day Divider Line Style", group = "Monday Settings")
Line_st               = inp_line_style == "Solid" ? line.style_solid : inp_line_style == "Dotted" ? line.style_dotted : inp_line_style == "Dashed" ? line.style_dashed : na
inp_line_style_fib    = input.string("Dotted", options = ["Dotted", "Solid", "Dashed"], title = "Fib Line Style", group = "Monday Settings")
Line_st_fib           = inp_line_style_fib == "Solid" ? line.style_solid : inp_line_style_fib == "Dotted" ? line.style_dotted : inp_line_style_fib == "Dashed" ? line.style_dashed : na
show_openingR         = input.string("Entire Week", options = ["Only on Monday", "Entire Week", "None","Tue-Sun"], title = "Show Monday Opening Range on", group = "Monday Settings")
Show_mday_OR          = show_openingR == "Tue-Sun" ? dayofweek == dayofweek.tuesday or dayofweek == dayofweek.wednesday or dayofweek == dayofweek.thursday or dayofweek == dayofweek.friday or dayofweek == dayofweek.saturday or dayofweek == dayofweek.sunday : show_openingR == "Only on Monday" ? dayofweek == dayofweek.monday : show_openingR == "Entire Week" ? dayofweek == dayofweek.monday or dayofweek == dayofweek.tuesday or dayofweek == dayofweek.wednesday or dayofweek == dayofweek.thursday or dayofweek == dayofweek.friday or dayofweek == dayofweek.saturday or dayofweek == dayofweek.sunday: na
dont_show_or          = show_openingR == "None" ? false :true

show_monday_HL        = input.string("Entire Week", options = ["Entire Week", "Only on Monday"], title = "Show Monday HL on", group = "Monday Settings")
Show_monday_HLset     = show_monday_HL == "Entire Week" ? friday_bar: na
dont_show_monday_HL   = show_monday_HL == "Only on Monday" ? false :true

show_breaks          = input.bool(false, 'Show breaks between days', group = "Monday Settings")
show_day_labels      = input.bool(false, 'Show day labels', group = "Monday Settings")
show_or_labels       = input.bool(false, 'Show OR label', group = "Monday Settings")
show_fibs            = input.bool(false, 'Show 0.618 and 0.382 Fibs', group = "Monday Settings")
show_price           = input.bool(true, 'Show Monday HL Price', group = "Monday Settings")
Show_prev_monday_OR  = input.bool(false, 'Show prev Monday OR (This will show when price is 2% away from pMDay Opening Range)', group = "Monday Settings")
show_Line_B          = input.bool(true, 'Show Anchored Weekly Line', group = "Weekly Anchored Trendline")

break_line_col       = input(defval=color.new(#565c70, 35),   title='Break Color', group = "Color Settings")
day_label_col        = input(defval=color.new(#afcff7, 50),   title='Day Label Color', group = "Color Settings")
Mon_lines            = input(defval=color.new(#565c70, 35),  title='Monday Line Color', group = "Color Settings")
Opening_R            = input(defval=color.new(#343946, 40),  title='Monday Opening Range color', group = "Color Settings")
fib_color            = input(defval=color.new(#565c70, 35),   title='Monday Fib Color', group = "Color Settings")
swing_warning_color  = input(defval=color.new(color.white, 0),   title='Warning Text color when breaching Mday H/L on Tuesday', group = "Color Settings")
line_col_theme       = input(defval=color.new(color.white, 70),   title='Monday Open to Close line', group = "Color Settings")


//Monday Anchored
new_period(p) => p and na(p[1])
sm = time(timeframe.period, "0000-0000:2")
var float c = close[1]

if new_period(sm)
    c := close   
if sm
    c := close

new_period2(p2) => p2 and na(p2[1])
sm2 = time(timeframe.period, "0000-0000:1")
var float c2 = close

if new_period2(sm2)
    c2 := time   
if sm2
    c2 := close     

mon_open_bar = ta.barssince(sm2)
mon_end_bar  = ta.barssince(sm)    

hide_right_oi        = time > sm  ? color.new(color.green, 0)   : color.new(color.yellow, 0) 


line_n = show_Line_B ? line.new(bar_index[mon_open_bar],c2,bar_index[mon_end_bar],c,color=color.new(color.green,100),width = 1, extend = extend.right, style = line.style_dotted):na
line.delete(line_n[1])

kkk = line.get_price(line_n,bar_index[1])

line_n1 = show_Line_B ? line.new(bar_index[mon_end_bar],c,bar_index[1],kkk,color=line_col_theme,width = 1, style = line.style_dotted):na
line.delete(line_n1[1])

[weeklyOpen, prev_weeklyOpen]    = request.security(syminfo.tickerid, 'W',   [open, open[1]], lookahead=barmerge.lookahead_on)

percentage_from_prev_wOpen = (close - prev_weeklyOpen)/prev_weeklyOpen *100
percentage_from_wOpen = (close - weeklyOpen)/weeklyOpen *100
high_low = close > prev_weeklyOpen ? low : close < prev_weeklyOpen ? high :na
fade_color = color.new(#6673a5, 98)
t_color    = color.new(#676d84,0)

percentage_range(value, minimum, maximum) =>
    math.min(math.max(value, minimum), maximum)
point_0_3 = percentage_range(percentage_from_prev_wOpen, -0.1, +0.1)
point_0_4 = percentage_range(percentage_from_prev_wOpen, -0.2, +0.2)
point_0_5 = percentage_range(percentage_from_prev_wOpen, -0.3, +0.3)
point_0_6 = percentage_range(percentage_from_prev_wOpen, -0.4, +0.4)
point_0_7 = percentage_range(percentage_from_prev_wOpen, -0.5, +0.5)
point_0_8 = percentage_range(percentage_from_prev_wOpen, -0.6, +0.6)
point_0_9 = percentage_range(percentage_from_prev_wOpen, -0.7, +0.7)

point_0_3t = percentage_range(percentage_from_wOpen, -0.1, +0.1)
point_0_4t = percentage_range(percentage_from_wOpen, -0.2, +0.2)
point_0_5t = percentage_range(percentage_from_wOpen, -0.3, +0.3)
point_0_6t = percentage_range(percentage_from_wOpen, -0.4, +0.4)
point_0_7t = percentage_range(percentage_from_wOpen, -0.5, +0.5)
point_0_8t = percentage_range(percentage_from_wOpen, -0.6, +0.6)
point_0_9t = percentage_range(percentage_from_wOpen, -0.7, +0.7)

point_0_3_away = point_0_3 == percentage_from_prev_wOpen ? true : false
point_0_4_away = point_0_4 == percentage_from_prev_wOpen ? true : false
point_0_5_away = point_0_5 == percentage_from_prev_wOpen ? true : false
point_0_6_away = point_0_6 == percentage_from_prev_wOpen ? true : false
point_0_7_away = point_0_7 == percentage_from_prev_wOpen ? true : false
point_0_8_away = point_0_8 == percentage_from_prev_wOpen ? true : false
point_0_9_away = point_0_9 == percentage_from_prev_wOpen ? true : false

point_0_3_awayt = point_0_3t == percentage_from_wOpen ? true : false
point_0_4_awayt = point_0_4t == percentage_from_wOpen ? true : false
point_0_5_awayt = point_0_5t == percentage_from_wOpen ? true : false
point_0_6_awayt = point_0_6t == percentage_from_wOpen ? true : false
point_0_7_awayt = point_0_7t == percentage_from_wOpen ? true : false
point_0_8_awayt = point_0_8t == percentage_from_wOpen ? true : false
point_0_9_awayt = point_0_9t == percentage_from_wOpen ? true : false

////////////////////////////////Open Dots////////////////////////////////////
show_a = timeframe.period == '1' or timeframe.period == '2'  or timeframe.period == '3'or timeframe.period == '4'or timeframe.period == '5'or timeframe.period == '6' or timeframe.period == '7'or timeframe.period == '8'or timeframe.period == '9'or timeframe.period == '10'or timeframe.period == '11'or timeframe.period == '12'or timeframe.period == '13'or timeframe.period == '14'or timeframe.period == '15'or timeframe.period == '20'or timeframe.period == '30'
show_b = timeframe.period == '1' or timeframe.period == '2'  or timeframe.period == '3'or timeframe.period == '4'or timeframe.period == '5'or timeframe.period == '6' or timeframe.period == '7'or timeframe.period == '8'or timeframe.period == '9'or timeframe.period == '10'or timeframe.period == '11'or timeframe.period == '12'or timeframe.period == '13'or timeframe.period == '14'or timeframe.period == '15'or timeframe.period == '20'or timeframe.period == '30'or timeframe.period == '60'or timeframe.period == '120'or timeframe.period == '240'
show_c = timeframe.period == '1' or timeframe.period == '2'  or timeframe.period == '3'or timeframe.period == '4'or timeframe.period == '5'or timeframe.period == '6' or timeframe.period == '7'or timeframe.period == '8'or timeframe.period == '9'or timeframe.period == '10'or timeframe.period == '11'or timeframe.period == '12'or timeframe.period == '13'or timeframe.period == '14'or timeframe.period == '15'or timeframe.period == '20'or timeframe.period == '30'or timeframe.period == '60'or timeframe.period == '120'or timeframe.period == '240'or timeframe.period == 'D'

i_open = input(true, 'Plot Open Dots', group= 'Open Dots')
i_open_c  = input(defval=color.new(color.white, 0),   title='Weekly Open color')
i_open_c2 = input(defval=color.new(color.red, 0),   title='Monthly Open color')
// i_open_c3 = input(defval=color.new(color.white, 0),   title='Yearly Open color')
// i_open_c4 = input(defval=color.new(color.white, 0),   title='Quarterly Open color')

open_level   = request.security(syminfo.tickerid, 'W', open, lookahead=barmerge.lookahead_on)
close_level  = request.security(syminfo.tickerid, 'W', close[1], lookahead=barmerge.lookahead_on)
open_level2  = request.security(syminfo.tickerid, 'M', open, lookahead=barmerge.lookahead_on)
close_level2 = request.security(syminfo.tickerid, 'M', close[1], lookahead=barmerge.lookahead_on)
open_level4  = request.security(syminfo.tickerid, '3M', open, lookahead=barmerge.lookahead_on)
close_level4 = request.security(syminfo.tickerid, '3M', close[1], lookahead=barmerge.lookahead_on)
open_level3  = request.security(syminfo.tickerid, '12M', open, lookahead=barmerge.lookahead_on)
close_level3 = request.security(syminfo.tickerid, '12M', close[1], lookahead=barmerge.lookahead_on)

new_day     = close_level[1] != close_level
new_day2    = close_level2[1] != close_level2
new_day3    = close_level3[1] != close_level3
new_day4    = close_level4[1] != close_level4

plotchar(new_day  and i_open and show_a ? open_level : na, title='Close', char='•', location=location.absolute, color=i_open_c, offset=0, size=size.tiny)
plotchar(new_day2 and i_open ? open_level2 : na, title='Close', char='•', location=location.absolute, color=i_open_c2, offset=0, size=size.tiny)


////////////////// Monday Box and fill////////////////////////

var datePrev = 0
var H = 0.0
var L = 0.0

date = time('D')
newDay1 = date != datePrev
datePrev := date

dow = dayofweek(date) + 1
bcolor = dow == dayofweek.tuesday ? Mon_lines : color.new(color.orange, 100)

H := newDay1 or high > H ? high[0] : H
L := newDay1 or low < L ? low[0] : L

pH = plot(show_a ? H:na, title='High', style=plot.style_stepline, linewidth=1, color=bcolor)
pL = plot(show_a ? L:na, title='Low', style=plot.style_stepline, linewidth=1, color=bcolor)

bcolor1ab = dow == dayofweek.wednesday ? color.white : color.new(color.orange, 100)
dope= color.new(#0c3299,100)
dope2= color.new(#0c3299,100)

is_monday = dayofweek == dayofweek.monday

float monday_high = 0
float monday_low = 0

highh = request.security(syminfo.tickerid, 'D', high)
loww = request.security(syminfo.tickerid, 'D', low)

monday_high := is_monday ? highh : monday_high[1]
monday_low := is_monday ? loww : monday_low[1]

between = (monday_low -400)
between2 = (monday_high +400)
isoutside = high > monday_high and high < between2

isoutside2 = low < monday_low and low > between
klo=isoutside and show_a  ? bcolor1ab : na
klo_Text_size =isoutside and show_a  ? size.normal : size.tiny
klo2=isoutside2 and show_a ? bcolor1ab : na

text_p = isoutside and show_a ? "WE JUST BREACHED MONDAY'S H ON TUESDAY" : isoutside2 and show_a ? "WE JUST BREACHED MONDAY'S L ON TUESDAY" :na
low_high = isoutside and show_a ? high : isoutside2 and show_a ? low :na
col_m = isoutside and show_a ? bcolor1ab : isoutside2 and show_a ? bcolor1ab :na

//////////////// IB Mon-Tue///////////
getIB(session_times) =>
    in_session = time(timeframe.period, session_times)
    var ib_high = 0.0
    var ib_low = 10e10
    if in_session
        if not in_session[1]
            ib_high := high
            ib_low := low
            ib_low
        else
            ib_high := math.max(high, ib_high)
            ib_low := math.min(low, ib_low)
            ib_low
    [in_session, ib_high, ib_low]

[in_day_session, ib_high, ib_low] = getIB(IB_D)

moday_bar_index = (monday_bar)
tuday_bar_index = (tuesday_bar)
weday_bar_index = (wednesday_bar)
thday_bar_index = (thursday_bar)
frday_bar_index = (friday_bar)

only_show_sunday_label_if_affter_saturday = sunday_bar < saturday_bar ? true : false
only_show_monday_label_if_affter_sunday = monday_bar < sunday_bar ? true : false
only_show_thuesday_label_if_affter_monday = tuesday_bar < monday_bar ? true : false
only_show_wednesday_label_if_affter_thuesday = wednesday_bar < monday_bar ? true : false
only_show_thursday_label_if_affter_wednesday = thursday_bar < monday_bar ? true : false
only_show_friday_label_if_affter_thursday = friday_bar < monday_bar ? true : false
only_show_saturday_label_if_affter_friday = saturday_bar < monday_bar? true : false

m = timeframe.period == '3' ? 240 : timeframe.period == '4' ? 177 : timeframe.period == '5' ? 144 : timeframe.period == '6' ? 117 : timeframe.period == '7' ? 101 : timeframe.period == '8' ? 87 : timeframe.period == '10' ? 72 : timeframe.period == '15' ? 48 : timeframe.period == '20' ? 36 : 0

move_monday_index_when_it_is_tuesday = dayofweek == dayofweek.monday ? 0 : m
move_tuesday_index_when_it_is_wednesday = dayofweek == dayofweek.tuesday ? 0 : m
move_wednesday_index_when_it_is_thursday = dayofweek == dayofweek.wednesday ? 0 : m
move_thursday_index_when_it_is_friday = dayofweek == dayofweek.thursday ? 0 : m
move_friday_index_when_it_is_saturday = dayofweek == dayofweek.friday ? 0 : m

hide_on_monday = dayofweek == dayofweek.monday ? false :true
hide_line_tuesday = dayofweek == dayofweek.tuesday ? false :true
hide_line_wednesday = dayofweek == dayofweek.wednesday ? false :true
hide_line_thursday = dayofweek == dayofweek.thursday ? false :true
hide_line_friday = dayofweek == dayofweek.friday ? false :true
hide_sunday = dayofweek == dayofweek.sunday ? false :true

monday_label = show_day_labels and hide_sunday  ? label.new(bar_index[moday_bar_index+move_monday_index_when_it_is_tuesday], monday_low, text="MONDAY",color=color.new(color.black,100),   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(monday_label[1])
tuesday_label = show_day_labels and only_show_thuesday_label_if_affter_monday and hide_sunday    ? label.new(bar_index[tuday_bar_index+move_tuesday_index_when_it_is_wednesday], monday_low, text="TUESDAY",color=color.new(color.black,100),   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(tuesday_label[1])
wednesday_label = show_day_labels and only_show_wednesday_label_if_affter_thuesday and hide_sunday  ? label.new(bar_index[weday_bar_index+move_wednesday_index_when_it_is_thursday], monday_low, text="WEDNESDAY",color=color.new(color.black,100),   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(wednesday_label[1])
thursday_label = show_day_labels and only_show_thursday_label_if_affter_wednesday and hide_sunday  ? label.new(bar_index[thday_bar_index+move_thursday_index_when_it_is_friday], monday_low, text="THURSDAY",color=color.new(color.black,100),   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(thursday_label[1])
friday_label = show_day_labels and only_show_friday_label_if_affter_thursday and hide_sunday    ? label.new(bar_index[frday_bar_index+move_friday_index_when_it_is_saturday], monday_low, text="FRIDAY",color=color.new(color.black,100),   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(friday_label[1])

devider_lines_tue= show_breaks and only_show_thuesday_label_if_affter_monday and hide_line_tuesday and hide_sunday  ? line.new(bar_index[tuesday_bar], monday_low, bar_index[tuesday_bar], monday_high, color=break_line_col, width=1,style=Line_st):na
line.delete(devider_lines_tue[1])
devider_lines_wed= show_breaks and only_show_wednesday_label_if_affter_thuesday and hide_line_wednesday and hide_sunday  ? line.new(bar_index[wednesday_bar], monday_low, bar_index[wednesday_bar], monday_high, color=break_line_col, width=1,style=Line_st):na
line.delete(devider_lines_wed[1])
devider_lines_thu= show_breaks and only_show_thursday_label_if_affter_wednesday and hide_line_thursday and hide_sunday  ? line.new(bar_index[thursday_bar], monday_low, bar_index[thursday_bar], monday_high, color=break_line_col, width=1,style=Line_st):na
line.delete(devider_lines_thu[1])
devider_lines_fri= show_breaks and only_show_friday_label_if_affter_thursday and hide_line_friday and hide_sunday ?  line.new(bar_index[friday_bar], monday_low, bar_index[friday_bar], monday_high, color=break_line_col, width=1,style=Line_st):na
line.delete(devider_lines_fri[1])

range2 = monday_high - monday_low
six_one_eight = monday_high  - 0.618 * range2
three_eight_two = monday_high  - 0.382 * range2

six_one_eight_line = show_fibs and only_show_thuesday_label_if_affter_monday and hide_sunday ? line.new(bar_index[monday_bar], six_one_eight, bar_index, six_one_eight, color=fib_color, width=1,style=Line_st_fib):na
line.delete(six_one_eight_line[1])
three_eight_two_line = show_fibs and only_show_thuesday_label_if_affter_monday and hide_sunday ? line.new(bar_index[monday_bar], three_eight_two, bar_index, three_eight_two, color=fib_color, width=1,style=Line_st_fib):na
line.delete(three_eight_two_line[1])

Opening_range_label_horizontal_pos = dayofweek == dayofweek.monday ? moday_bar_index : dayofweek == dayofweek.tuesday ? tuday_bar_index : dayofweek == dayofweek.wednesday ? weday_bar_index : dayofweek == dayofweek.thursday ? thday_bar_index : dayofweek == dayofweek.friday ? frday_bar_index :na

text_monday_or = dont_show_or and show_or_labels and only_show_monday_label_if_affter_sunday and hide_sunday  ? label.new(bar_index[Opening_range_label_horizontal_pos], (ib_high+ib_low)/2, text="MONDAY OPENING RANGE  |  "+str.tostring((ib_high+ib_low)/2),color=color.new(color.black,100),   textcolor=day_label_col, size=TextSize,style=label.style_label_left):na
label.delete(text_monday_or[1])

text_monday_H = dont_show_or  and only_show_monday_label_if_affter_sunday and hide_sunday and show_price  ? label.new(bar_index[Opening_range_label_horizontal_pos], monday_high, text="H  |  "+str.tostring(monday_high),color=color.new(color.black,100),   textcolor=day_label_col, size=TextSize,style=label.style_label_left):na
label.delete(text_monday_H[1])
text_monday_L = dont_show_or  and only_show_monday_label_if_affter_sunday and hide_sunday and show_price ? label.new(bar_index[Opening_range_label_horizontal_pos], monday_low, text="L  |  "+str.tostring(monday_low),color=color.new(color.black,100),   textcolor=day_label_col, size=TextSize,style=label.style_label_left):na
label.delete(text_monday_L[1])

Monday_H_line = dont_show_monday_HL and only_show_thuesday_label_if_affter_monday and hide_sunday ? line.new(bar_index[monday_bar], monday_high, bar_index, monday_high, color=Mon_lines, width=1,style=line.style_solid):na
line.delete(Monday_H_line[1])
Monday_L_line = dont_show_monday_HL and only_show_thuesday_label_if_affter_monday and hide_sunday ? line.new(bar_index[monday_bar], monday_low, bar_index, monday_low, color=Mon_lines, width=1,style=line.style_solid):na
line.delete(Monday_L_line[1])

mlabel = label.new(bar_index-1, (ib_high+ib_low)/2, text=text_p, color=color.new(color.black,100), style=label.style_label_right, textcolor=col_m, size=TextSize, textalign="left")
label.delete(mlabel[1])
//////////////// IB Mon-Tue///////////
bcolor55 = dow == Show_mday_OR ? color.new(color.orange, 100) : Opening_R
day_ib_start = plot(true and show_a and Show_mday_OR ? ib_high : na, title='IB High Line', color=color.new(color.blue, 100), linewidth=1, style=plot.style_stepline)
day_ib_end = plot(true and show_a and Show_mday_OR ? ib_low : na, title='IB Low Line', color=color.new(color.blue, 100), linewidth=1, style=plot.style_stepline)
fill(day_ib_start, day_ib_end, color=bcolor55, title='IB Background')

// ALERTS =====================================================================

if  ta.cross(close,monday_high) 
    alert("Price crossed Monday's L/H", alert.freq_once_per_bar)

// if ta.cross(close,ib_high) or ta.cross(close,ib_low)
//     alert("Price crossed Monday's Opening Range", alert.freq_once_per_bar)

```

## Comments and planning