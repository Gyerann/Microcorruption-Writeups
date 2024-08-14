OVERVIEW

    - This lock is attached the the LockIT Pro HSM-2.
    - We have updated  the lock firmware to connect with this hardware
      security module.


DETAILS

    The LockIT Pro c.01  is the first of a new series  of locks. It is
    controlled by a  MSP430 microcontroller, and is  the most advanced
    MCU-controlled lock available on the  market. The MSP430 is a very
    low-power device which allows the LockIT  Pro to run in almost any
    environment.

    The  LockIT  Pro   contains  a  Bluetooth  chip   allowing  it  to
    communiciate with the  LockIT Pro App, allowing the  LockIT Pro to
    be inaccessable from the exterior of the building.

    There  is no  default  password  on the  LockIT  Pro HSM-2.   Upon
    receiving the  LockIT Pro,  a new  password must  be set  by first
    connecting the LockitPRO HSM to  output port two, connecting it to
    the LockIT Pro App, and entering a new password when prompted, and
    then restarting the LockIT Pro using the red button on the back.
    
    LockIT Pro Hardware  Security Module 2 stores  the login password,
    ensuring users  can not access  the password through  other means.
    The LockIT Pro  can send the LockIT Pro HSM-2  a password, and the
    HSM will  directly send the  correct unlock message to  the LockIT
    Pro Deadbolt  if the password  is correct, otherwise no  action is
    taken.
    
    This is Hardware  Version C.  It contains  the Bluetooth connector
    built in, and two available  ports: the LockIT Pro Deadbolt should
    be  connected to  port  1,  and the  LockIT  Pro  HSM-2 should  be
    connected to port 2.

    This is  Software Revision  01. The firmware  has been  updated to
    connect with the new hardware security module. We have removed the
    function to unlock the door from the LockIT Pro firmware.

-------------------------------
Key takeaway:
HSM-2

Notes:
If conditional_unlock_door return 1 in r15 lock gets opened
Input password stored at 3e82

Primitives:
Password is said to be 8-16 chars long but buffer is 48 bytes

Given a larger input than the intended 16 chars we can overwrite code

36 hex chars of input can be anything, afterwards it gets executed

aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa1012000090120000
