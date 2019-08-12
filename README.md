# TTT
TTT macro

# method
3ring param...//return value to $00.
```
 //user memory $01-$0Z
//memory array $$$ for LOG
//global memory gVal[key]=value
```
big eye
```
@sample1 //start address
{{{
 ...cut in the javascript
}}}
LOG $00 $$$
```

```
XYZ param1 param2//cmd XYZ
$00 //special memory $$$ is XYZ return value.
$01=xxx //memory to $01
$01={{{5+6+7}}} //javascript direct wrap {{{...}}}. like the same. function(){return 5+6+7}
$01?#1 //if($A0) jump to #1
CHK $01===8 //if(A0===8) memory to $00
$00?#1
LOG $00 $$$//like a same console.log. return value not catched.
//canable comment double slash. dont use the astrisk wrap. /* ... */
@sample1 //address name @sample1

<<< #1 //sub address #1. full address @sample1#1
//the loop.
>>> #1 

{{{ 
let a=function(d){ console.log(d) }
TTT.cmd("LO2",a,[void 0]) //cmd definition. cmd,funciton,defaultArguments
}}} 
```
