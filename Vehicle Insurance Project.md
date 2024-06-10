```R
5+5
```


```R
setwd("~/02_Corporate Profile/Project Portfolio/Vehicle Insurance Data")
```


```R
motor_data_2014_2018 = read.csv("~/02_Corporate Profile/Project Portfolio/Vehicle Insurance Data/motor_data14-2018.csv")

```


```R
str(motor_data_2014_2018)
```

    'data.frame':	508499 obs. of  16 variables:
     $ SEX              : int  0 0 0 0 0 0 0 0 1 1 ...
     $ INSR_BEGIN       : Factor w/ 1461 levels "01-APR-15","01-APR-16",..: 344 343 342 341 344 343 342 341 1144 1143 ...
     $ INSR_END         : Factor w/ 1691 levels "01-APR-15","01-APR-16",..: 345 344 343 342 345 344 343 342 1265 1264 ...
     $ EFFECTIVE_YR     : Factor w/ 140 levels "","-1","-2","-6",..: 21 21 21 21 21 21 21 21 27 27 ...
     $ INSR_TYPE        : int  1202 1202 1202 1202 1202 1202 1202 1202 1202 1202 ...
     $ INSURED_VALUE    : num  519755 519755 519755 519755 1400000 ...
     $ PREMIUM          : num  5098 6557 6557 5103 13305 ...
     $ OBJECT_ID        : num  5e+09 5e+09 5e+09 5e+09 5e+09 ...
     $ PROD_YEAR        : int  2007 2007 2007 2007 2010 2010 2010 2010 2012 2012 ...
     $ SEATS_NUM        : int  4 4 4 4 4 4 4 4 0 0 ...
     $ CARRYING_CAPACITY: num  6 6 6 6 7 7 7 7 220 220 ...
     $ TYPE_VEHICLE     : Factor w/ 11 levels "Automobile","Bus",..: 4 4 4 4 4 4 4 4 11 11 ...
     $ CCM_TON          : num  3153 3153 3153 3153 2494 ...
     $ MAKE             : Factor w/ 746 levels " BEBIEN TANKER",..: 475 475 475 475 616 616 616 616 324 324 ...
     $ USAGE            : Factor w/ 14 levels "Agricultural Any Farm",..: 10 10 10 10 10 10 10 10 7 7 ...
     $ CLAIM_PAID       : num  NA NA NA NA NA ...
    


```R
colnames(motor_data_2014_2018)
```


<ol class=list-inline>
	<li>'SEX'</li>
	<li>'INSR_BEGIN'</li>
	<li>'INSR_END'</li>
	<li>'EFFECTIVE_YR'</li>
	<li>'INSR_TYPE'</li>
	<li>'INSURED_VALUE'</li>
	<li>'PREMIUM'</li>
	<li>'OBJECT_ID'</li>
	<li>'PROD_YEAR'</li>
	<li>'SEATS_NUM'</li>
	<li>'CARRYING_CAPACITY'</li>
	<li>'TYPE_VEHICLE'</li>
	<li>'CCM_TON'</li>
	<li>'MAKE'</li>
	<li>'USAGE'</li>
	<li>'CLAIM_PAID'</li>
</ol>




```R
head(motor_data_2014_2018)
```


<table>
<thead><tr><th scope=col>SEX</th><th scope=col>INSR_BEGIN</th><th scope=col>INSR_END</th><th scope=col>EFFECTIVE_YR</th><th scope=col>INSR_TYPE</th><th scope=col>INSURED_VALUE</th><th scope=col>PREMIUM</th><th scope=col>OBJECT_ID</th><th scope=col>PROD_YEAR</th><th scope=col>SEATS_NUM</th><th scope=col>CARRYING_CAPACITY</th><th scope=col>TYPE_VEHICLE</th><th scope=col>CCM_TON</th><th scope=col>MAKE</th><th scope=col>USAGE</th><th scope=col>CLAIM_PAID</th></tr></thead>
<tbody>
	<tr><td>0         </td><td>08-AUG-17 </td><td>07-AUG-18 </td><td>08        </td><td>1202      </td><td> 519755.2 </td><td> 5097.83  </td><td>5000029885</td><td>2007      </td><td>4         </td><td>6         </td><td>Pick-up   </td><td>3153      </td><td>NISSAN    </td><td>Own Goods </td><td>NA        </td></tr>
	<tr><td>0         </td><td>08-AUG-16 </td><td>07-AUG-17 </td><td>08        </td><td>1202      </td><td> 519755.2 </td><td> 6556.52  </td><td>5000029885</td><td>2007      </td><td>4         </td><td>6         </td><td>Pick-up   </td><td>3153      </td><td>NISSAN    </td><td>Own Goods </td><td>NA        </td></tr>
	<tr><td>0         </td><td>08-AUG-15 </td><td>07-AUG-16 </td><td>08        </td><td>1202      </td><td> 519755.2 </td><td> 6556.52  </td><td>5000029885</td><td>2007      </td><td>4         </td><td>6         </td><td>Pick-up   </td><td>3153      </td><td>NISSAN    </td><td>Own Goods </td><td>NA        </td></tr>
	<tr><td>0         </td><td>08-AUG-14 </td><td>07-AUG-15 </td><td>08        </td><td>1202      </td><td> 519755.2 </td><td> 5102.83  </td><td>5000029885</td><td>2007      </td><td>4         </td><td>6         </td><td>Pick-up   </td><td>3153      </td><td>NISSAN    </td><td>Own Goods </td><td>NA        </td></tr>
	<tr><td>0         </td><td>08-AUG-17 </td><td>07-AUG-18 </td><td>08        </td><td>1202      </td><td>1400000.0 </td><td>13304.87  </td><td>5000029901</td><td>2010      </td><td>4         </td><td>7         </td><td>Pick-up   </td><td>2494      </td><td>TOYOTA    </td><td>Own Goods </td><td>NA        </td></tr>
	<tr><td>0         </td><td>08-AUG-16 </td><td>07-AUG-17 </td><td>08        </td><td>1202      </td><td>1400000.0 </td><td>16438.15  </td><td>5000029901</td><td>2010      </td><td>4         </td><td>7         </td><td>Pick-up   </td><td>2494      </td><td>TOYOTA    </td><td>Own Goods </td><td>NA        </td></tr>
</tbody>
</table>




```R

```
