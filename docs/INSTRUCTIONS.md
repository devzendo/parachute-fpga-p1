# Supported Instructions

I'd like to support all instructions needed by eForth - the FPGA I'm using is very small.



The instructions **in bold** are used by eForth and are those I hope to support. There are only 28 needed - although eForth currently does not support communications to an Iserver over its link 0, for which **outbyte** and **in** would also be needed, and possibly **out** - so possibly 30 instructions.



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

