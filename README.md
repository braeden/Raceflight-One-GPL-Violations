# Raceflight-One GPL Violations

```
unzip BF and RF
cd RaceFlight-One-current/
find . -type f -print0 | xargs -0 mv -t ~/Downloads/GPL\ Raceflight/raceflight_files/
cd ..
cd betaflight-3.0.1/
find . -type f -print0 | xargs -0 mv -t ~/Downloads/GPL\ Raceflight/betaflight_files/

./moss.pl -d betaflight_files/*.c betaflight_files/*.h raceflight_files/*.c raceflight_files/*.h
```
-------

## https://docs.google.com/document/d/1QK1PC5cYST8B6NynXUeIji1pmg9fQmY0WqoSsv4gnFo/edit

--------

Results here: (This will expire in 14 days, I will publish the folders that I submitted)
http://moss.stanford.edu/results/587590701/

https://theory.stanford.edu/~aiken/moss/

If you want to look for more violations yourself -  you'll want to verify that they are not shared pieces of code, like device drivers, math libraries etc. Take this all with a grain of salt, and assume that I screwed something up. But I'm pretty certain we can find GPL violation proof here.

---------
 
**While a large majority of the codebase has been re-written or refactored, I think the combination of these finds at least highly suggest the use of GPL Betaflight code within the closed-source Raceflight releases. I have no qualms against Kalyan, and I think it’s incredibly impressive to write it nearly from scratch. I also have no interest in legal action, since there is such a miniscule overlap.**

## BUT, the purpose of this repository is to prove Preston’s claims of an entirely re-written codebase are factually incorrect. 


| Raceflight Code | Betaflight Code | Comments |
| ------------- | ------------- | ------------ |
| https://github.com/rs2k/RaceFlight-One/blob/6b541c85eaa3d391f1e26950a498e9bad9dddc9f/src/flight_controller/src/filter.c#L504 (Lines 504-511) | https://github.com/betaflight/betaflight/blob/0e827b331d05e5cc12304f6278a3ded26c2a2f20/src/main/common/filter.c#L99 (Lines 99-106) | The comments are exactly the same. “// precompute the coefficients” and “// zero initial samples”The math is and layout is exactly the same, except with different variable names.
https://github.com/rs2k/RaceFlight-One/blob/6b541c85eaa3d391f1e26950a498e9bad9dddc9f/src/flight_controller/src/filter.c#L527 (Lines 527-533) | https://github.com/betaflight/betaflight/blob/0e827b331d05e5cc12304f6278a3ded26c2a2f20/src/main/common/filter.c#L40 (Lines 40-44) | Exact same layout and spacing of the math. The same variable names. Only difference is that the function inputs are switched.
https://github.com/rs2k/RaceFlight-One/blob/6b541c85eaa3d391f1e26950a498e9bad9dddc9f/src/flight_controller/src/filter.c#L467 (Lines 467-484) | https://github.com/betaflight/betaflight/blob/0e827b331d05e5cc12304f6278a3ded26c2a2f20/src/main/common/filter.c#L80 (Lines 80-97) |  Switch statement with the same input variable. Nearly the same case names. Exactly the same variable names and math in identical order within each case.

