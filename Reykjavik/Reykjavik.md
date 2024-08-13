Lockitall                                            LOCKIT PRO r a.03
______________________________________________________________________

              User Manual: Lockitall LockIT Pro, rev a.03              
______________________________________________________________________


OVERVIEW

    - Lockitall developers  have implemented  military-grade on-device
      encryption to keep the password secure.
    - This lock is not attached to any hardware security module.


DETAILS

    The LockIT Pro a.03  is the first of a new series  of locks. It is
    controlled by a  MSP430 microcontroller, and is  the most advanced
    MCU-controlled lock available on the  market. The MSP430 is a very
    low-power device which allows the LockIT  Pro to run in almost any
    environment.

    The  LockIT  Pro   contains  a  Bluetooth  chip   allowing  it  to
    communiciate with the  LockIT Pro App, allowing the  LockIT Pro to
    be inaccessable from the exterior of the building.

    There is  no default password  on the LockIT  Pro---upon receiving
    the LockIT Pro, a new password must be set by connecting it to the
    LockIT Pro  App and  entering a password  when prompted,  and then
    restarting the LockIT Pro using the red button on the back.
    
    This is Hardware  Version A.  It contains  the Bluetooth connector
    built in, and one available port  to which the LockIT Pro Deadbolt
    should be connected.

    This is Software Revision 02. This release contains military-grade
    encryption so users can be confident that the passwords they enter
    can not be read from memory.   We apologize for making it too easy
    for the password to be recovered on prior versions.  The engineers
    responsible have been sacked.

---------------------------------------

Now theres an ecryption function as well

do nothing seemingly does something

enc function fills memory at 0x2400 with:
2400: 0b12 0412 0441 2452 3150 e0ff 3b40 2045   .....A$R1P..;@ E
2410: 073c 1b53 8f11 0f12 0312 b012 6424 2152   .<.S........d$!R
2420: 6f4b 4f93 f623 3012 0a00 0312 b012 6424   oKO..#0.......d$
2430: 2152 3012 1f00 3f40 dcff 0f54 0f12 2312   !R0...?@...T..#.
2440: b012 6424 3150 0600 b490 1c5f dcff 0520   ..d$1P....._... 
2450: 3012 7f00 b012 6424 2153 3150 2000 3441   0....d$!S1P .4A
2460: 3b41 3041 1e41 0200 0212 0f4e 8f10 024f   ;A0A.A.....N...O
2470: 32d0 0080 b012 1000 3241 3041 d21a 189a   2.......2A0A....
2480: 22dc 45b9 4279 2d55 858e a4a2 67d7 14ae   ".E.By-U....g...
2490: a119 76f6 42cb 1c04 0efa a61b 74a7 416b   ..v.B.......t.Ak
24a0: d237 a253 22e4 66af c1a5 938b 8971 9b88   .7.S".f......q..
24b0: fa9b 6674 4e21 2a6b b143 9151 3dcc a6f5   ..ftN!*k.C.Q=...
24c0: daa7 db3f 8d3c 4d18 4736 dfa6 459a 2461   ...?.<M.G6..E.$a
24d0: 921d 3291 14e6 8157 b0fe 2ddd 400b 8688   ..2....W..-.@...
24e0: 6310 3ab3 612b 0bd9 483f 4e04 5870 4c38   c.:.a+..H?N.XpL8
24f0: c93c ff36 0e01 7f3e fa55 aeef 051c 242c   .<.6..>.U....$,
2500: 3c56 13af e57b 8abf 3040 c537 656e 8278   <V...{..0@.7en.x
2510: 9af9 9d02 be83 b38c e181 3ad8 395a fce3   ..........:.9Z..
2520: 4f03 8ec9 9395 4a15 ce3b fd1e 7779 c9c3   O.....J..;..wy..
2530: 5ff2 3dc7 5953 8826 d0b5 d9f8 639e e970   _.=.YS.&....c..p
2540: 01cd 2119 ca6a d12c 97e2 7538 96c5 8f28   ..!..j.,..u8...(
2550: d682 1be5 ab20 7389 48aa 1fa3 472f a564   ..... s.H...G/.d
2560: de2d b710 9081 5205 8d44 cff4 bc2e 577a   .-....R..D....Wz
2570: d5f4 a851 c243 277d a4ca 1e6b

---------------

enc writes numbers from 0 to 256 to memory at 0x247c (character set)
ThisIsSecureRight? in memory at 4472
the the character set gets shuffled based on key:
ThisIsSecureRight?
Then getts shuffled again

Then enc function returns and bytecode at 2400 gets executed
 
2400: 0b12 0412 0441 2452 3150 e0ff 3b40 2045   .....A$R1P..;@ E
2410: 073c 1b53 8f11 0f12 0312 b012 6424 2152   .<.S........d$!R
2420: 6f4b 4f93 f623 3012 0a00 0312 b012 6424   oKO..#0.......d$
2430: 2152 3012 1f00 3f40 dcff 0f54 0f12 2312   !R0...?@...T..#.
2440: b012 6424 3150 0600 b490 1c5f dcff 0520   ..d$1P....._... 
2450: 3012 7f00 b012 6424 2153 3150 2000 3441   0....d$!S1P .4A
2460: 3b41 3041 1e41 0200 0212 0f4e 8f10 024f   ;A0A.A.....N...O
2470: 32d0 0080 b012 1000 3241 3041

0b120412044124523150e0ff3b402045073c1b538f110f120312b012642421526f4b4f93f62330120a000312b0126424215230121f003f40dcff0f540f122312b012642431500600b4901c5fdcff052030127f00b012642421533150200034413b4130411e41020002120f4e8f10024f32d00080b012100032413041

2400    0b12           push	r11
        0412           push	r4
        0441           mov	sp, r4
        2452           add	#0x4, r4
        3150 e0ff      add	#0xffe0, sp
        3b40 2045      mov	#0x4520, r11    #Whats the password? string
2410    073c           jmp	$+0x10
        1b53           inc	r11
        8f11           sxt	r15
        0f12           push	r15
        0312           push	#0x0
        b012 6424      call	#0x2464         #Call put_char
        2152           add	#0x4, sp
2420    6f4b           mov.b	@r11, r15
        4f93           tst.b	r15
        f623           jnz	$-0x12
        3012 0a00      push	#0xa
        0312           push	#0x0
        b012 6424      call	#0x2464
2430    2152           add	#0x4, sp
        3012 1f00      push	#0x1f
        3f40 dcff      mov	#0xffdc, r15
        0f54           add	r4, r15
        0f12           push	r15
        2312           push	#0x2
2440    b012 6424      call	#0x2464
        3150 0600      add	#0x6, sp
        b490 1c5f dcff cmp	#0x5f1c, -0x24(r4)
        0520           jnz	$+0xc
2450    3012 7f00      push	#0x7f
        b012 6424      call	#0x2464
        2153           incd	sp
        3150 2000      add	#0x20, sp
        3441           pop	r4
2460    3b41           pop	r11
        3041           ret

        <put_char>
2464    1e41 0200      mov	0x2(sp), r14
        0212           push	sr
        0f4e           mov	r14, r15
        8f10           swpb	r15
        024f           mov	r15, sr
2470    32d0 0080      bis	#0x8000, sr
        b012 1000      call	#0x10
        3241           pop	sr
        3041           ret

From 247c:
d21a 189a   2.......2A0A....
2480: 22dc 45b9 4279 2d55 858e a4a2 67d7 14ae   ".E.By-U....g...
2490: a119 76f6 42cb 1c04 0efa a61b 74a7 416b   ..v.B.......t.Ak
24a0: d237 a253 22e4 66af c1a5 938b 8971 9b88   .7.S".f......q..
24b0: fa9b 6674 4e21 2a6b b143 9151 3dcc a6f5   ..ftN!*k.C.Q=...
24c0: daa7 db3f 8d3c 4d18 4736 dfa6 459a 2461   ...?.<M.G6..E.$a
24d0: 921d 3291 14e6 8157 b0fe 2ddd 400b 8688   ..2....W..-.@...
24e0: 6310 3ab3 612b 0bd9 483f 4e04 5870 4c38   c.:.a+..H?N.XpL8
24f0: c93c ff36 0e01 7f3e fa55 aeef 051c 242c   .<.6..>.U....$,
2500: 3c56 13af e57b 8abf 3040 c537 656e 8278   <V...{..0@.7en.x
2510: 9af9 9d02 be83 b38c e181 3ad8 395a fce3   ..........:.9Z..
2520: 4f03 8ec9 9395 4a15 ce3b fd1e 7779 c9c3   O.....J..;..wy..
2530: 5ff2 3dc7 5953 8826 d0b5 d9f8 639e e970   _.=.YS.&....c..p
2540: 01cd 2119 ca6a d12c 97e2 7538 96c5 8f28   ..!..j.,..u8...(
2550: d682 1be5 ab20 7389 48aa 1fa3 472f a564   ..... s.H...G/.d
2560: de2d b710 9081 5205 8d44 cff4 bc2e 577a   .-....R..D....Wz
2570: d5f4 a851 c243 277d a4ca 1e6b 0000 0000

d21a189a22dc45b942792d55858ea4a267d714aea11976f642cb1c040efaa61b74a7416bd237a25322e466afc1a5938b89719b88fa9b66744e212a6bb14391513dcca6f5daa7db3f8d3c4d184736dfa6459a2461921d329114e68157b0fe2ddd400b868863103ab3612b0bd9483f4e0458704c38c93cff360e017f3efa55aeef051c242c3c5613afe57b8abf3040c537656e82789af99d02be83b38ce1813ad8395afce34f038ec993954a15ce3bfd1e7779c9c35ff23dc759538826d0b5d9f8639ee97001cd2119ca6ad12c97e2753896c58f28d6821be5ab20738948aa1fa3472fa564de2db710908152058d44cff4bc2e577ad5f4a851c243277da4ca1e6b00000000

input is saved to 43da

