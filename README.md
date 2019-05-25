# Candlestick_patterns

This project is to identify candlestick patterns, there are two ways of doing it.

1. pass the OHLC of last 3 candles, it will return the bullish score and candle pattern.

l_0=[10560.35,10582.35	,10527.45	,10564.05]
l_1=[10592.8	,10638.35	,10514.95	,10584.7]
l_2=[10578.1	,10636.8	,10569.0	,10614.35]

score,pattern=candle_score(l_0,l_1,l_2)

output is (0, 'doji')

2. Another way is to pass the pandas dataframe and it will return the dataframe with two more columns "candle_pattern" and "candle_score"


import pandas as pd
import numpy as np
from nsepy import get_history
import datetime

to_dt=datetime.datetime.now().date()
from_dt=to_dt-datetime.timedelta(days=20)

df=get_history('NIFTY',from_dt,to_dt,index=True)

df=candle_df(df)

df[:][['candle_pattern','candle_score']]

Output is:>
                            candle_pattern  candle_score
Date                                                    
2019-05-22            doji/ Bullish_Harami             1
2019-05-23             / Bearish_Engulfing            -1
2019-05-24                / Bullish_Harami             1
