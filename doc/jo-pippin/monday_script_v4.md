# Summary 
Locates Mondays and extend through Tuesday. Shows Opening range and warning when Monday H/L is breached on Tuesday 

# Indicator overview
* Locates Mondays and extend through Tuesday. 
* Shows Opening range and warning when Monday H/L is breached on Tuesday 

![description](./assets/monday_script_v4/description.png?raw=true)

# Code Snippets 

```pine

//Jo-Pippin 
//@version=5
indicator(title='Mondays | Opens V4', shorttitle='Mondays | Opens V4', overlay=true , max_bars_back = 500)

sunday_bar             = ta.barssince(dayofweek == dayofweek.sunday)
monday_bar             = ta.barssince(dayofweek == dayofweek.monday)
tuesday_bar            = ta.barssince(dayofweek == dayofweek.tuesday)
wednesday_bar          = ta.barssince(dayofweek == dayofweek.wednesday)
thursday_bar           = ta.barssince(dayofweek == dayofweek.thursday)
friday_bar             = ta.barssince(dayofweek == dayofweek.friday)
saturday_bar           = ta.barssince(dayofweek == dayofweek.saturday)

inp_text_size          = input.string("Tiny", options = ["Tiny", "Small","Normal"], title = "Text Sizs", group = "Monday Settings")
TextSize               = inp_text_size == "Tiny" ? size.tiny : inp_text_size == "Small" ? size.small : inp_text_size == "Normal" ? size.normal : na
inp_line_style         = input.string("Dotted", options = ["Dotted", "Solid", "Dashed"], title = "Day Divider Line Style", group = "Monday Settings")
Line_st                = inp_line_style == "Solid" ? line.style_solid : inp_line_style == "Dotted" ? line.style_dotted : inp_line_style == "Dashed" ? line.style_dashed : na
inp_line_style_fib     = input.string("Dotted", options = ["Dotted", "Solid", "Dashed"], title = "Fib Line Style", group = "Monday Settings")
Line_st_fib            = inp_line_style_fib == "Solid" ? line.style_solid : inp_line_style_fib == "Dotted" ? line.style_dotted : inp_line_style_fib == "Dashed" ? line.style_dashed : na
show_openingR          = input.string("Entire Week", options = ["Only on Monday", "Entire Week", "None","Tue-Sun"], title = "Show Monday Opening Range on", group = "Monday Settings")
Show_mday_OR           = show_openingR == "Tue-Sun" ? dayofweek == dayofweek.tuesday or dayofweek == dayofweek.wednesday or dayofweek == dayofweek.thursday or dayofweek == dayofweek.friday or dayofweek == dayofweek.saturday or dayofweek == dayofweek.sunday : show_openingR == "Only on Monday" ? dayofweek == dayofweek.monday : show_openingR == "Entire Week" ? dayofweek == dayofweek.monday or dayofweek == dayofweek.tuesday or dayofweek == dayofweek.wednesday or dayofweek == dayofweek.thursday or dayofweek == dayofweek.friday or dayofweek == dayofweek.saturday or dayofweek == dayofweek.sunday: na
dont_show_or           = show_openingR == "None" ? false :true

show_monday_HL         = input.string("Entire Week", options = ["Entire Week", "Only on Monday"], title = "Show Monday HL on", group = "Monday Settings")
Show_monday_HLset      = show_monday_HL == "Entire Week" ? friday_bar: na
dont_show_monday_HL    = show_monday_HL == "Only on Monday" ? false :true

show_breaks            = input.bool(true, 'Show breaks between days', group = "Monday Settings")
show_day_labels        = input.bool(true, 'Show day labels', group = "Monday Settings")
show_or_labels         = input.bool(true, 'Show Opening Range label', group = "Monday Settings")
show_fibs              = input.bool(true, 'Show 0.618 and 0.382 Fibs', group = "Monday Settings")
show_price             = input.bool(true, 'Show Monday HL Price', group = "Monday Settings")
show_weekly_candle     = input.bool(true, 'Show Weekly Candle On the right', group = "Monday Settings")
show_daily_candle      = input.bool(true, 'Show Daily Candle On the right', group = "Monday Settings")
i_open                 = input.bool(true, 'Plot Weekly Open Dots', group = "Monday Settings")
show_vol_candle        = input.bool(true, 'Show Max Vol candle measured from the start of this week', group = "Volume & OI Settings")
show_oi_candle         = input.bool(true, 'Show Max OI % change up and down candles measured from the start of this week', group = "Volume & OI Settings")
show_oi_wcandle        = input.bool(true, 'Show Max OI % change up and down on side weekly candle', group = "Volume & OI Settings")
show_vol_wcandle       = input.bool(true, 'Show Max volume on side weekly candle', group = "Volume & OI Settings")
weekly_ext             = input.int (50,   'Extend Weekly Candle Left or right',  minval=1, maxval=3000, group = "Volume & OI Settings")
daily_ext              = input.int (30,   'Extend Daily Candle Left or right',  minval=1, maxval=3000, group = "Volume & OI Settings")
wick_width             = input.int (1,    'Volume and OI Candle Wick width on existing candles',     minval=1, maxval=30, group = "Volume & OI Settings")
body_width             = input.int (4,    'Volume and OI Candle Body width on existing candles',     minval=1, maxval=30, group = "Volume & OI Settings")

break_line_col         = input(defval=color.new(#565c70, 35),    title='Day Break Color', group = "Color Settings")
day_label_col          = input(defval=color.new(#afcff7, 50),    title='Day Label Color', group = "Color Settings")
Mon_lines              = input(defval=color.new(#565c70, 35),    title='Monday Line Color', group = "Color Settings")
Opening_R              = input(defval=color.new(#343946, 40),    title='Monday Opening Range color', group = "Color Settings")
fib_color              = input(defval=color.new(#565c70, 35),    title='Monday Fib Color', group = "Color Settings")
i_open_c               = input(defval=color.new(color.white, 0), title='Open Dots color', group = "Color Settings")
Rise_c                 = input.color(color.new(#44fa3e, 0),'OI Rise Candle Color', group = "Color Settings")
Fall_c                 = input.color(color.new(#fd4444, 0),'OI FallCandle Color', group = "Color Settings")
candle_c               = input.color(color.new(#3179f5, 0),'Volume Candle Color', group = "Color Settings")
w_candle_c             = input.color(color.new(#6d80a1, 23),'Weekly and Daily side Candle Color', group = "Color Settings")


[dl,dh,day_open,dc]         = request.security(syminfo.tickerid, 'D', expression=[low,high,open,close])
[wo,wc1,wl,wh,wc]      = request.security(syminfo.tickerid, 'W', expression=[open, close[1],low,high,close], lookahead=barmerge.lookahead_on)

//Weekly Start Bars to current
is_newbarw(resw) =>
    tw = time(resw)
    ta.change(tw) != 0 ? 1 : 0

firstcandlew=is_newbarw("D") and is_newbarw("W")

var countDw = 0
countDw := is_newbarw("W") ? 1 : is_newbarw("D") ? countDw + 1 : countDw

is_week = countDw==1
week_bars_back = ta.barssince(is_week)

//Vol input
arr = array.new_float(0)
for i = 1 to week_bars_back by 1

	array.push(arr, (volume[i]))

first_Highest = array.max(arr, 0)
first_Highest_index = array.lastindexof(arr, first_Highest)

//OI input
[oiO,oiC] = request.security("BTCPERP_OI +BTCUSDTPERP_OI",timeframe.period, expression=[open,close])
			   
arr_oi = array.new_float(0)
for i = 1 to week_bars_back by 1
	
	array.push(arr_oi, (oiO[i]-oiC[i]))

first_Highest_oi = array.max(arr_oi, 0)
First_Lowest_oi = array.min(arr_oi, 0)

first_Highest_index_oi = array.lastindexof(arr_oi, first_Highest_oi)
first_Lowest_index_oi = array.lastindexof(arr_oi, First_Lowest_oi)

tostring_alert = first_Highest_index  == 0 ? "Weekly volume on the M" + str.tostring(timeframe.period) + " candle just shifted to the current candle" : 
 first_Highest_index_oi               == 0 ? "The largest OI fall for the week on the M" + str.tostring(timeframe.period) + " candle just shifted to the current candle" :
 first_Lowest_index_oi                == 0 ? "The largest OI rise for the week on the M" + str.tostring(timeframe.period) + " candle just shifted to the current candle" :
 first_Highest_index                  == 0 and first_Highest_index_oi == 0 ? "The largest OI fall and volume spike for the week on the M" + str.tostring(timeframe.period) + " candle just shifted to the current candle" : 
 first_Highest_index                  == 0 and first_Lowest_index_oi  == 0 ? "The largest OI rise and volume spike for the week on the M" + str.tostring(timeframe.period) + " candle just shifted to the current candle" : na

if first_Highest_index == 0 or first_Highest_index_oi == 0 or first_Lowest_index_oi==0
    
    alert(tostring_alert, alert.freq_once_per_bar_close)

// alertcondition(first_Highest_index == 0 or first_Highest_index_oi == 0 or first_Lowest_index_oi==0, title='Volume or OI shift', message='Volume or OI shifted to the current bar. Could be a pivot!')

////////////////////////////////Open Dots////////////////////////////////////
dont_show_on_ltfs = timeframe.period == '3' ? true : 
 timeframe.period == '4' ? true : 
 timeframe.period == '5' ? true : 
 timeframe.period == '6' ? true : 
 timeframe.period == '7' ? true : 
 timeframe.period == '8' ? true : 
 timeframe.period == '9' ? true : 
 timeframe.period == '10' ? true : 
 timeframe.period == '11' ? true : 
 timeframe.period == '12' ? true :
 timeframe.period == '13' ? true : 
 timeframe.period == '14' ? true : 
 timeframe.period == '15' ? true :
 false

new_day     = wc1[1]  != wc1

//Monday Outlines
transparent = color.new(color.orange, 100)

var datePrev = 0
var H = 0.0
var L = 0.0

date = time('D')
newDay1 = date != datePrev
datePrev := date

bcolor = dayofweek == dayofweek.monday ? Mon_lines : transparent

H := newDay1 or high > H ? high[0] : H
L := newDay1 or low  < L ? low[0]  : L

pH = plot(H, title='High', style=plot.style_stepline, linewidth=1, color=bcolor)
pL = plot(L, title='Low' , style=plot.style_stepline, linewidth=1, color=bcolor)

Show_Monday_Warning_Color_Hide = dayofweek == dayofweek.thursday ? color.white : transparent
is_monday = dayofweek == dayofweek.monday

float monday_high = 0
float monday_low = 0

monday_high := is_monday ? dh : monday_high[1]
monday_low  := is_monday ? dl : monday_low[1]

//////////////// IB Mon-Tue///////////
getIB(session_times) =>
    in_session  = time(timeframe.period, session_times)
    var ib_high = 0.0
    var ib_low  = 10e10
    if in_session
        if not in_session[1]
            ib_high := high
            ib_low  := low
            ib_low
        else
            ib_high := math.max(high, ib_high)
            ib_low  := math.min(low, ib_low)
            ib_low
    [in_session, ib_high, ib_low]

[in_day_session, ib_high, ib_low] = getIB('0000-0005:2')

//Display Day Label In right order
only_show_sunday_label_if_affter_saturday    = sunday_bar    < saturday_bar ? true : false
only_show_monday_label_if_affter_sunday      = monday_bar    < sunday_bar   ? true : false
only_show_thuesday_label_if_affter_monday    = tuesday_bar   < monday_bar   ? true : false
only_show_wednesday_label_if_affter_thuesday = wednesday_bar < monday_bar   ? true : false
only_show_thursday_label_if_affter_wednesday = thursday_bar  < monday_bar   ? true : false
only_show_friday_label_if_affter_thursday    = friday_bar    < monday_bar   ? true : false
only_show_saturday_label_if_affter_friday    = saturday_bar  < monday_bar   ? true : false

//Shift Day Labels to midle of session per timeframe 
Shift_days_to_middle = timeframe.period == '3' ? 240 : 
     timeframe.period == '4'  ? 177 : 
     timeframe.period == '5'  ? 144 : 
     timeframe.period == '6'  ? 117 : 
     timeframe.period == '7'  ? 101 : 
     timeframe.period == '8'  ? 87  : 
     timeframe.period == '10' ? 72  : 
     timeframe.period == '15' ? 48  : 
     timeframe.period == '20' ? 36  : 0

move_monday_index_when_it_is_tuesday     = dayofweek == dayofweek.monday    ? 0 : Shift_days_to_middle
move_tuesday_index_when_it_is_wednesday  = dayofweek == dayofweek.tuesday   ? 0 : Shift_days_to_middle
move_wednesday_index_when_it_is_thursday = dayofweek == dayofweek.wednesday ? 0 : Shift_days_to_middle
move_thursday_index_when_it_is_friday    = dayofweek == dayofweek.thursday  ? 0 : Shift_days_to_middle
move_friday_index_when_it_is_saturday    = dayofweek == dayofweek.friday    ? 0 : Shift_days_to_middle

//Hide days
hide_on_monday      = dayofweek == dayofweek.monday    ? false :true
hide_line_tuesday   = dayofweek == dayofweek.tuesday   ? false :true
hide_line_wednesday = dayofweek == dayofweek.wednesday ? false :true
hide_line_thursday  = dayofweek == dayofweek.thursday  ? false :true
hide_line_friday    = dayofweek == dayofweek.friday    ? false :true
hide_sunday         = dayofweek == dayofweek.sunday    ? false :true

//Fib calc
Monday_mid_price = monday_high  - monday_low
six_one_eight    = monday_high  - 0.618 * Monday_mid_price
three_eight_two  = monday_high  - 0.382 * Monday_mid_price

//Weekday Labels
monday_label    = dont_show_on_ltfs and show_day_labels and hide_sunday  ? label.new(bar_index[monday_bar+move_monday_index_when_it_is_tuesday], monday_low, text="MONDAY",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(monday_label[1])
tuesday_label   = dont_show_on_ltfs and show_day_labels and only_show_thuesday_label_if_affter_monday and hide_sunday    ? label.new(bar_index[tuesday_bar+move_tuesday_index_when_it_is_wednesday], monday_low, text="TUESDAY",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(tuesday_label[1])
wednesday_label = dont_show_on_ltfs and show_day_labels and only_show_wednesday_label_if_affter_thuesday and hide_sunday  ? label.new(bar_index[wednesday_bar+move_wednesday_index_when_it_is_thursday], monday_low, text="WEDNESDAY",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(wednesday_label[1])
thursday_label  = dont_show_on_ltfs and show_day_labels and only_show_thursday_label_if_affter_wednesday and hide_sunday  ? label.new(bar_index[thursday_bar+move_thursday_index_when_it_is_friday], monday_low, text="THURSDAY",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(thursday_label[1])
friday_label    = dont_show_on_ltfs and show_day_labels and only_show_friday_label_if_affter_thursday and hide_sunday    ? label.new(bar_index[friday_bar+move_friday_index_when_it_is_saturday], monday_low, text="FRIDAY",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(friday_label[1])

//Weekday Deviders
devider_lines_tue  = dont_show_on_ltfs and show_breaks and only_show_thuesday_label_if_affter_monday and hide_line_tuesday and hide_sunday  ? line.new(bar_index[tuesday_bar], monday_low, bar_index[tuesday_bar], monday_high, color=break_line_col, width=1,style=Line_st):na
line.delete(devider_lines_tue[1])
devider_lines_wed  =  dont_show_on_ltfs and show_breaks and only_show_wednesday_label_if_affter_thuesday and hide_line_wednesday and hide_sunday  ? line.new(bar_index[wednesday_bar], monday_low, bar_index[wednesday_bar], monday_high, color=break_line_col, width=1,style=Line_st):na
line.delete(devider_lines_wed[1])
devider_lines_thu  = dont_show_on_ltfs and show_breaks and only_show_thursday_label_if_affter_wednesday and hide_line_thursday and hide_sunday  ? line.new(bar_index[thursday_bar], monday_low, bar_index[thursday_bar], monday_high, color=break_line_col, width=1,style=Line_st):na
line.delete(devider_lines_thu[1])
devider_lines_fri  = dont_show_on_ltfs and show_breaks and only_show_friday_label_if_affter_thursday and hide_line_friday and hide_sunday ?  line.new(bar_index[friday_bar], monday_low, bar_index[friday_bar], monday_high, color=break_line_col, width=1,style=Line_st):na
line.delete(devider_lines_fri[1])

//Fibs
six_one_eight_line   = dont_show_on_ltfs and show_fibs and only_show_thuesday_label_if_affter_monday and hide_sunday ? line.new(bar_index[monday_bar], six_one_eight, bar_index, six_one_eight, color=fib_color, width=1,style=Line_st_fib):na
line.delete(six_one_eight_line[1])
three_eight_two_line = dont_show_on_ltfs and show_fibs and only_show_thuesday_label_if_affter_monday and hide_sunday ? line.new(bar_index[monday_bar], three_eight_two, bar_index, three_eight_two, color=fib_color, width=1,style=Line_st_fib):na
line.delete(three_eight_two_line[1])

//Opening Range Label
Opening_range_label_horizontal_pos = dayofweek == dayofweek.monday ? monday_bar : dayofweek == dayofweek.tuesday ? tuesday_bar : dayofweek == dayofweek.wednesday ? wednesday_bar : dayofweek == dayofweek.thursday ? thursday_bar : dayofweek == dayofweek.friday ? friday_bar :na
text_monday_or = dont_show_on_ltfs and dont_show_or and show_or_labels and only_show_monday_label_if_affter_sunday and hide_sunday  ? label.new(bar_index[Opening_range_label_horizontal_pos], (ib_high+ib_low)/2, text= "Mday OR  |  "+str.tostring((ib_high+ib_low)/2) ,color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_left):na
label.delete(text_monday_or[1])

//Monday HL labels
text_monday_H = dont_show_on_ltfs and dont_show_or  and only_show_monday_label_if_affter_sunday and hide_sunday and show_price  ? label.new(bar_index[Opening_range_label_horizontal_pos], monday_high, text="H  |  "+str.tostring(monday_high) ,color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_left):na
label.delete(text_monday_H[1])
text_monday_L = dont_show_on_ltfs and dont_show_or  and only_show_monday_label_if_affter_sunday and hide_sunday and show_price ? label.new(bar_index[Opening_range_label_horizontal_pos], monday_low, text="L  |  "+str.tostring(monday_low),color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_left):na
label.delete(text_monday_L[1])

//Monday HL lines
Monday_H_line = dont_show_on_ltfs and dont_show_monday_HL and only_show_thuesday_label_if_affter_monday and hide_sunday ? line.new(bar_index[monday_bar], monday_high, bar_index, monday_high, color=Mon_lines, width=1,style=line.style_solid):na
line.delete(Monday_H_line[1])
Monday_L_line = dont_show_on_ltfs and dont_show_monday_HL and only_show_thuesday_label_if_affter_monday and hide_sunday ? line.new(bar_index[monday_bar], monday_low, bar_index, monday_low, color=Mon_lines, width=1,style=line.style_solid):na
line.delete(Monday_L_line[1])

//Vol Candle
candle_body = dont_show_on_ltfs and show_vol_candle ? line.new(bar_index[first_Highest_index+1], open[first_Highest_index+1], bar_index[first_Highest_index+1], close[first_Highest_index+1], color=candle_c, width=body_width):na
line.delete(candle_body[1])
candle_wick = dont_show_on_ltfs and show_vol_candle ?  line.new(bar_index[first_Highest_index+1], high[first_Highest_index+1], bar_index[first_Highest_index+1], low[first_Highest_index+1], color=candle_c, width=wick_width):na
line.delete(candle_wick[1])

//OI Candles up
candle_body_oi_up  = dont_show_on_ltfs and show_oi_candle ? line.new(bar_index[first_Highest_index_oi+1], open[first_Highest_index_oi+1], bar_index[first_Highest_index_oi+1], close[first_Highest_index_oi+1], color=Fall_c, width=body_width):na
line.delete(candle_body_oi_up  [1])
candle_wick_oi_up  = dont_show_on_ltfs and show_oi_candle ? line.new(bar_index[first_Highest_index_oi+1], high[first_Highest_index_oi+1], bar_index[first_Highest_index_oi+1], low[first_Highest_index_oi+1], color=Fall_c, width=wick_width):na
line.delete(candle_wick_oi_up  [1])

//OI Candles down
candle_body_oi_down  = dont_show_on_ltfs and show_oi_candle ? line.new(bar_index[first_Lowest_index_oi+1], open[first_Lowest_index_oi+1], bar_index[first_Lowest_index_oi+1], close[first_Lowest_index_oi+1], color=Rise_c, width=body_width):na
line.delete(candle_body_oi_down  [1])
candle_wick_oi_down  = dont_show_on_ltfs and show_oi_candle ? line.new(bar_index[first_Lowest_index_oi+1], high[first_Lowest_index_oi+1], bar_index[first_Lowest_index_oi+1], low[first_Lowest_index_oi+1], color=Rise_c, width=wick_width):na
line.delete(candle_wick_oi_down  [1])

//Weekly Side Candle OI and Vol
   ///Volume onWeekly Candle
candle_body_w_vol = dont_show_on_ltfs and show_weekly_candle and show_vol_wcandle      ? line.new(bar_index+weekly_ext, high[first_Highest_index+1], bar_index+weekly_ext, low[first_Highest_index+1], color=candle_c , width=2):na
line.delete(candle_body_w_vol[1])
   ///OI close - open onWeekly Candle
candle_body_w_oi_up = dont_show_on_ltfs and show_weekly_candle and show_oi_wcandle    ? line.new(bar_index+weekly_ext, high[first_Highest_index_oi+1], bar_index+weekly_ext, low[first_Highest_index_oi+1], color=Fall_c , width=2):na
line.delete(candle_body_w_oi_up[1])
    ///OI high - low onWeekly Candle   
candle_body_w_oi_down = dont_show_on_ltfs and show_weekly_candle and show_oi_wcandle  ? line.new(bar_index+weekly_ext, high[first_Lowest_index_oi+1], bar_index+weekly_ext, low[first_Lowest_index_oi+1], color= Rise_c, width=2):na
line.delete(candle_body_w_oi_down[1])


//Weekly Side Candle
candle_wick_w = dont_show_on_ltfs and show_weekly_candle        ?  line.new(bar_index+weekly_ext, wh, bar_index+weekly_ext, wl, color=w_candle_c, width=1):na
line.delete(candle_wick_w[1])

candle_close_w = dont_show_on_ltfs and show_weekly_candle       ?  line.new(bar_index+weekly_ext, wc, bar_index+weekly_ext+3, wc, color=w_candle_c, width=1):na
line.delete(candle_close_w[1])


candle_close_w_label = dont_show_on_ltfs and show_weekly_candle ? label.new(bar_index+weekly_ext+3, wc, text=" wc",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_left):na
label.delete(candle_close_w_label[1])

candle_high_w_label = dont_show_on_ltfs and show_weekly_candle  ? label.new(bar_index+weekly_ext, wh, text=" wh",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_down):na
label.delete(candle_high_w_label[1])
candle_low_w_label = dont_show_on_ltfs and show_weekly_candle   ? label.new(bar_index+weekly_ext, wl, text=" wl",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(candle_low_w_label[1])

candle_open_w_label = dont_show_on_ltfs and show_weekly_candle  ? label.new(bar_index+weekly_ext-3, wo, text="wo ",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_right):na
label.delete(candle_open_w_label[1])
candle_open_w = dont_show_on_ltfs and show_weekly_candle        ?  line.new(bar_index+weekly_ext-3, wo, bar_index+weekly_ext, wo, color=w_candle_c, width=1):na
line.delete(candle_open_w[1])


//Daily Side Candle
candle_wick_d = dont_show_on_ltfs and show_daily_candle        ?  line.new(bar_index+weekly_ext+daily_ext, dh, bar_index+weekly_ext+daily_ext, dl, color=w_candle_c, width=1):na
line.delete(candle_wick_d[1])

candle_close_d = dont_show_on_ltfs and show_daily_candle        ?  line.new(bar_index+weekly_ext+daily_ext, dc, bar_index+weekly_ext+daily_ext+3, dc, color=w_candle_c, width=1):na
line.delete(candle_close_d[1])

candle_close_d_label = dont_show_on_ltfs and show_daily_candle  ? label.new(bar_index+weekly_ext+daily_ext+3, dc, text=" dc",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_left):na
label.delete(candle_close_d_label[1])
candle_high_d_label = dont_show_on_ltfs and show_daily_candle   ? label.new(bar_index+weekly_ext+daily_ext, dh, text=" dh",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_down):na
label.delete(candle_high_d_label[1])
candle_low_d_label = dont_show_on_ltfs and show_daily_candle    ? label.new(bar_index+weekly_ext+daily_ext, dl, text=" dl",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_up):na
label.delete(candle_low_d_label[1])

candle_open_d_label = dont_show_on_ltfs and show_daily_candle   ? label.new(bar_index+weekly_ext+daily_ext-3, day_open, text="do ",color=transparent,   textcolor=day_label_col, size=TextSize,style=label.style_label_right):na
label.delete(candle_open_d_label[1])

candle_open_d = dont_show_on_ltfs and show_daily_candle         ?  line.new(bar_index+weekly_ext+daily_ext-3, day_open, bar_index+weekly_ext+daily_ext, day_open, color=w_candle_c, width=1):na
line.delete(candle_open_d[1])

/// IB 
IB_hide_col     = dayofweek == Show_mday_OR ? transparent : Opening_R
day_ib_start    = plot(true and Show_mday_OR ? ib_high : na, title='IB High Line', color=transparent, linewidth=1, style=plot.style_stepline)
day_ib_end      = plot(true and Show_mday_OR ? ib_low  : na, title='IB Low Line' , color=transparent, linewidth=1, style=plot.style_stepline)
fill(day_ib_start, day_ib_end, color=IB_hide_col, title='IB Background')

/// Weekly Dots
plotchar(dont_show_on_ltfs and new_day  and i_open  ? wo : na, title='Close', char='⋅', location=location.absolute, color=i_open_c, offset=0, size=size.tiny)
plotchar(dont_show_on_ltfs and new_day  and i_open  ? wo : na, title='Close', char='ʷ', location=location.abovebar, color=i_open_c, offset=0, size=size.tiny)

```

## Comments and planning