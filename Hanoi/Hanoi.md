OVERVIEW

    - This lock is attached the the LockIT Pro HSM-1.
    - We have updated  the lock firmware  to connect with the hardware
      security module.


DETAILS

    The LockIT Pro b.01  is the first of a new series  of locks. It is
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

    This is Software Revision 01,  allowing it to communicate with the
    LockIT Pro HSM-1
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
441c:  9f4f 0c46 0024 mov	0x460c(r15), 0x2400(r15)
4422:  f923           jnz	$-0xc <__do_copy_data+0x8>
4424 <__do_clear_bss>
4424:  3f40 2200      mov	#0x22, r15
4428:  0f93           tst	r15
442a:  0624           jz	$+0xe <main+0x0>
442c:  8245 5c01      mov	r5, &0x015c
4430:  1f83           dec	r15
4432:  cf43 0024      mov.b	#0x0, 0x2400(r15)
4436:  fa23           jnz	$-0xa <__do_clear_bss+0x8>
4438 <main>
4438:  b012 2045      call	#0x4520 <login>
443c:  0f43           clr	r15
443e <__stop_progExec__>
443e:  32d0 f000      bis	#0xf0, sr
4442:  fd3f           jmp	$-0x4 <__stop_progExec__+0x0>
4444 <__ctors_end>
4444:  3040 0a46      br	#0x460a <_unexpected_>
4448 <unlock_door>
4448:  3012 7f00      push	#0x7f
444c:  b012 7a45      call	#0x457a <INT>
4450:  2153           incd	sp
4452:  3041           ret
4454 <test_password_valid>
4454:  0412           push	r4
4456:  0441           mov	sp, r4
4458:  2453           incd	r4
445a:  2183           decd	sp
445c:  c443 fcff      mov.b	#0x0, -0x4(r4)
4460:  3e40 fcff      mov	#0xfffc, r14
4464:  0e54           add	r4, r14
4466:  0e12           push	r14
4468:  0f12           push	r15
446a:  3012 7d00      push	#0x7d
446e:  b012 7a45      call	#0x457a <INT>
4472:  5f44 fcff      mov.b	-0x4(r4), r15
4476:  8f11           sxt	r15
4478:  3152           add	#0x8, sp
447a:  3441           pop	r4
447c:  3041           ret
447e .strings:
447e: "Enter the password to continue."
449e: "Remember: passwords are between 8 and 16 characters."
44d3: "Testing if password is valid."
44f1: "Access granted."
4501: "That password is not correct."
451f: ""
4520 <login>
4520:  c243 1024      mov.b	#0x0, &0x2410
4524:  3f40 7e44      mov	#0x447e "Enter the password to continue.", r15
4528:  b012 de45      call	#0x45de <puts>
452c:  3f40 9e44      mov	#0x449e "Remember: passwords are between 8 and 16 characters.", r15
4530:  b012 de45      call	#0x45de <puts>
4534:  3e40 1c00      mov	#0x1c, r14
4538:  3f40 0024      mov	#0x2400, r15
453c:  b012 ce45      call	#0x45ce <getsn>
4540:  3f40 0024      mov	#0x2400, r15
4544:  b012 5444      call	#0x4454 <test_password_valid>
4548:  0f93           tst	r15
454a:  0324           jz	$+0x8 <login+0x32>
454c:  f240 9e00 1024 mov.b	#0x9e, &0x2410
4552:  3f40 d344      mov	#0x44d3 "Testing if password is valid.", r15
4556:  b012 de45      call	#0x45de <puts>
455a:  f290 3e00 1024 cmp.b	#0x3e, &0x2410
4560:  0720           jnz	$+0x10 <login+0x50>
4562:  3f40 f144      mov	#0x44f1 "Access granted.", r15
4566:  b012 de45      call	#0x45de <puts>
456a:  b012 4844      call	#0x4448 <unlock_door>
456e:  3041           ret
4570:  3f40 0145      mov	#0x4501 "That password is not correct.", r15
4574:  b012 de45      call	#0x45de <puts>
4578:  3041           ret
457a <INT>
457a:  1e41 0200      mov	0x2(sp), r14
457e:  0212           push	sr
4580:  0f4e           mov	r14, r15
4582:  8f10           swpb	r15
4584:  024f           mov	r15, sr
4586:  32d0 0080      bis	#0x8000, sr
458a:  b012 1000      call	#0x10
458e:  3241           pop	sr
4590:  3041           ret
4592 <putchar>
4592:  2183           decd	sp
4594:  0f12           push	r15
4596:  0312           push	#0x0
4598:  814f 0400      mov	r15, 0x4(sp)
459c:  b012 7a45      call	#0x457a <INT>
45a0:  1f41 0400      mov	0x4(sp), r15
45a4:  3150 0600      add	#0x6, sp
45a8:  3041           ret
45aa <getchar>
45aa:  0412           push	r4
45ac:  0441           mov	sp, r4
45ae:  2453           incd	r4
45b0:  2183           decd	sp
45b2:  3f40 fcff      mov	#0xfffc, r15
45b6:  0f54           add	r4, r15
45b8:  0f12           push	r15
45ba:  1312           push	#0x1
45bc:  b012 7a45      call	#0x457a <INT>
45c0:  5f44 fcff      mov.b	-0x4(r4), r15
45c4:  8f11           sxt	r15
45c6:  3150 0600      add	#0x6, sp
45ca:  3441           pop	r4
45cc:  3041           ret
45ce <getsn>
45ce:  0e12           push	r14
45d0:  0f12           push	r15
45d2:  2312           push	#0x2
45d4:  b012 7a45      call	#0x457a <INT>
45d8:  3150 0600      add	#0x6, sp
45dc:  3041           ret
45de <puts>
45de:  0b12           push	r11
45e0:  0b4f           mov	r15, r11
45e2:  073c           jmp	$+0x10 <puts+0x14>
45e4:  1b53           inc	r11
45e6:  8f11           sxt	r15
45e8:  0f12           push	r15
45ea:  0312           push	#0x0
45ec:  b012 7a45      call	#0x457a <INT>
45f0:  2152           add	#0x4, sp
45f2:  6f4b           mov.b	@r11, r15
45f4:  4f93           tst.b	r15
45f6:  f623           jnz	$-0x12 <puts+0x6>
45f8:  3012 0a00      push	#0xa
45fc:  0312           push	#0x0
45fe:  b012 7a45      call	#0x457a <INT>
4602:  2152           add	#0x4, sp
4604:  0f43           clr	r15
4606:  3b41           pop	r11
4608:  3041           ret
460a <_unexpected_>
460a:  0013           reti	pc
--------------------------------
