# TTT
TTT command

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
NLD NowLoading... sub //
...
CLR sub //erase loading
@sample1 //address name @sample1

<<< #1 //sub address #1. full address @sample1#1
//the loop.
>>> #1 

{{{ 
let a=function(d){ console.log(d) }
TTT.cmd("LO2",a,[void 0]) //cmd definition. cmd,funciton,defaultArguments
}}} 
```




#tick loop
```
let tick=function(_fps,_fn){
 if(!_fn){throw new TypeError('tick(_fps,_fn);_fn is null');return}
 let i=0,imax=Number.MAX_SAFE_INTEGER - (Number.MAX_SAFE_INTEGER%10),safetick=()=>(i===imax)?1:i++
 ,fps=Math.max(_fps||1000/200,1000/200),fn=_fn;
 setInterval({ _fn(safetick()) },fps);
}

```
#layer
```
L00 x y z://L00 default layer 0 0 0 z is z-index
L01 100 100 10://new layer
L01 100 100 12://overwrite layer
DRW loading //default L00
DRW loading L01// x100 y100 z12
DSW L01 //show. same mean DSW L01 1
DSW L01 0//hide
DCR L01 //L00 empty, L01... delete layer L01
DCR //alive the L00 only not empty. other layer delete.
```

#MaDaM
```
//Mark Down Macro

#name //mdm macro
##name //javascript 
###name //document
```
#Mxx系
```
Mxx :MaDaM system order
 MDM:system info
 MAM:MaDaM Man command
 MAN:same Man command
Pxx :preload order
 PIM :preload Image file
 PTE :preload Text file 
$xx :memory order
 $00...$99
 $00: prepend functions return.
 $01?xyz:exist jump
 $01=xyz:input xyz to $00
Lxx :layer order
 L00...L99
 L00 :main layer never-ever delete.
 LOG ://special case console.log
Dxx :drawing order
 DRW
 DSW
 DCR
>>> :arrow jump
<<< :
{{{ :javascript wrap
}}} :javascript wrap
Exx :equal
 EQL A B: check the return $00
 EQL A B C: equal and jump to C.
 EXS $01 :exist $01 return $00
 EXS $01 C:exist and jump to C.
```

