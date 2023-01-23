# Supported Instructions

I'd like to support all instructions needed by eForth - the FPGA I'm using is very small.



The instructions **in bold** are used by eForth and are those I hope to support. There are only 28 needed - although eForth currently does not support communications to an Iserver over its link 0, for which **outbyte** and **in** would also be needed, and possibly **out** - so possibly 30 instructions.



# Survey of all real Transputer instructions

## Direct Instructions
**adc**, **ajw**, call, **cj**, **eqc**, **j**, **ldc**, **ldl**, ldlp, **ldnl**, ldnlp, **nfix**, **opr**, **pfix**, **stl**, **stnl**.

## Operations
add, alt, altend, altwt, **and**, bcnt, bitclt, bitrevnbits, bitrevword, bsub, ccnt1, **clrhalterr**, csngl, csub0, cword, diff, disc, diss, dist, div, **dup**, enbc, enbs, enbt, endp, fmul, **gajw**, **gcall**, gt, in, ladd, **lb**, ldiff, ldiv, **ldpi**, ldpri, ldtimer, lend, lmul, lshl, lshr, lsub, **lsum**, **mint**, **move**, mul, norm, **not**, **or**, out, outbyte, outword, prod, rem, resetch, ret, **rev**, runp, saveh, savel, **sb**, seterr, sethalterr, shl, shr, startp, sthb, **sthf**, stlb, **stlf**, stoperr, stopp, sttimer, sub, **sum**, talt, taltwt, **testerr**, testhalterr, testpranal, tin, **wcnt**, wsub, wsubdb, xdble, **xor**, xword.

_wcnt_ is only needed when waiting for a UART, which will not be needed if we support in/out.

_stlf, sthf, clrhalterr, testerr_ are currently used by eForth during init, but since P1 is not providing the facilities they control, they can be treated as a no-op; better still, ignored by the assembler if a _.P1_ pragma is introduced.

## T414

cflerr, ldinf, postnormsn, roundsn, unpacksn.

## T800

crcbyte, crcword, move2dall, move2dinit, move2dnonzero, move2dzero.

fpadd, fpb32tor64, fpchkerr, fpchki32, fpdiv, fpdup,fpentry, fpeq, fpgt,
fpi32tor32, fpi32tor64, fpint, fpldnladddb, fpldnladdsn, fpldnldb, fpldnldbi,
fpldnlmuldb, fpldnlmulsn, fpldnlsn, fpldnlsni, fpldzerodb, fpldzerosn, fpmul,
fpnan, fpnotfinite, fpordered, fpremfirst, fpremstep, fprev, fprtoi32, fpstnldb,
fpstnli32, fpstnlsn, fpsub, fptesterr, fpuabs, fpuchki64, fpuclrerr, fpudivby2, fpuexpdec32, fpuexpinc32, fpumulby2, fpunoround, fpur32tor64, fpur64tor32, fpurm, fpurn, fpurp, fpurz, fpuseterr, fpusqrtfirst,
fpusqrtlast, fpusqrtstep.

## T805

break, **clrj0break**, lddevid, ldmemstartval, pop, setj0break, testj0break, timerenableh, timerenablel, **timerdisableh**, **timerdisablel**.

These are used by eForth during init, but since P1 is not providing the facilities they control, they can be treated as a no-op; better still, ignored by the assembler if a _.P1_ pragma is introduced.

## T801
start, testhardchan, testldd, testlde, testlds, teststd, testste, teststs.

## T810

checkaddr, delay, dislinkinth, dislinkintl, distimesl, enlinkinth, enlinkintl,
entimesl, fpmacc, fpxprod, ldhw, macc, pause, sthw, xprod



# P1 Instructions Summary

The byte sequences given here are from Appendix E from The Compiler Writer's Guide.

## Direct instructions

| Byte | Abbreviation | Description      |
| ---- | ------------ | ---------------- |
| #0x  | j            | jump             |
| #2x  | pfix         | prefix           |
| #3x  | ldnl         | load non local   |
| #4x  | ldc          | load constant    |
| #6x  | nfix         | negative prefix  |
| #7x  | ldl          | load local       |
| #8x  | adc          | add constant     |
| #Ax  | cj           | conditional jump |
| #Bx  | ajw          | adjust workspace |
| #Cx  | eqc          | equals constant  |
| #Dx  | stl          | store non local  |
| #Ex  | stnl         | store non local  |
| #Fx  | opr          | operate          |

## Operations

| Bytes | Abbreviation | Description      |
| ----- | ------------ | ---------------- |
| #F0    |rev|reverse|
| #F1 |lb|load byte|
| #F6 |gcall|general call|
| #F7 |in (maybe)|input message|
| #FB |out (maybe)|output message|
| #FE |outbyte (maybe)|output byte|
| #FF |outword (maybe)|output word|
| #21;#FB |ldpi|load pointer to instruction|
| #23;#F2 |not|bitwise not|
| #23;#F3 |xor|exclusive or|
| #23;#F7 |lsum|long sum|
| #23;#FB |sb|store byte|
| #23;#FC |gajw|general adjust workspace|
| #23;#FF |wcnt (maybe)|word count|
| #24;#F2 |mint|minimum integer|
| #24;#F6 |and|and|
| #24;#FA |move|move message|
| #24;#FB |or|or|
| #25;#F2 |sum|sum|
| #25;#FA |dup|duplicate top of stack|



# P1 Instructions Specification

The specification makes reference to definitions in Appendix F from The Compiler Writer's Guide. I'm using the definitions in that appendix for these instruction specifications. The intention of this section is to enumerate all the machine state and operations needed to support the macroarchitecture and the microarchitecture needed to fetch and execute it. This will be used to define the data and control path.

## Registers and Nomenclature

Areg

Breg

Creg

Oreg

Iptr

Wptr

Oreg^o^ - the value of the operand register after decoding has taken place but before the selected instruction is executed.

*X*reg' - the value of the *X* register after the instruction whereas *X*reg represent the value of *X*  before the instruction. 

*NextInst* - the address of the start of the next instruction in the code.



## j - #0x - jump

(to be continued...)

