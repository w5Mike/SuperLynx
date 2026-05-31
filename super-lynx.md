# \*\*\* SUPER LYNX \*\*\*

Following on from the first LYNX USER SHOW in Birmingham recently where the beginnings of new ideas were being born, it is proposed that although the LYNX is already a superb home micro, it still has various gaps in its conception. It is a very under-developed, under-supported, and poorly understood machine. In fact one might wonder whether CAMPUTER's really saw the incredible potential buried in its design. It was and still is a really radical design concept with even now only a few micro manufacturers beginning to use some of the ideas which were implemented over 2 years ago in the "baby" LYNX. After all how many of today's micros use more than 2 pages of memory in their design? With the assistance and agreement of the LYNX's new owners, ANSTON TECHNOLOGY LTD), we as a dedicated user group have virtually a "free reign" to enhance and implement new ideas and improvements into the LYNX micro-computer. This CANNOT be said for any other machine on the market, where the manufacturers have used to keep production costs down, "funny chips"! These are of course dedicated ULAs, in this respect, I and many others are eternally grateful that the engineers stuck to 'LS TTL devices. This does help in "re-hashing" certain aspects of the LYNX's design. The plan is therefore to build into the LYNX as far as possible, as many "bells and whistles" as the machine will take.

The \*\*\*SUPER LYNX\*\*\* concept consists of three main areas:-

1. A large pcb which plugs into the main LYNX pcb and therefore "collects" several essential signals from the main LYNX system. On this pcb will be three areas of circuitry;
   - a) 8 sideways ROM slots (either 64K or 128K ROMs can be fitted);
   - b) The serial circuitry with the communication connector being the standard 25 pin "D" connector. This does mean cutting a slot into the rear of the LYNX plastic case;
   - c) The circuitry necessary for switching the LYNX into 64 and 80 column modes (GREEN only). Thus 4 different screen displays can be achieved, i.e. 32, 40 columns in all colours and 64, 80 columns in green only.

   There are also several minor modifications which will be required, so it is unlikely that the average LYNX owner will be able to implement the system successfully.

2. Thanks to the greatly expanded ROM space, a large range of new commands will be provided. See the list which follows.

3. Because of the increased power requirement, a new power supply will be included with higher ratings, plus the provision of a -12 volt rail primarily required for the RS232 standard.

Other "extras" are being considered like increased sound volume and provision for an external speaker.

What follows is a listing of possible extensions to the BASIC, but this is only a provisional list at present.

The following list gives some idea of the range of new commands which is hoped would be implemented in the ROM's:-

## New Commands

| Command | Description |
|---|---|
| **RENUM x,y** | Increased power, which would allow re-numbering from line number "x" to the end of memory. RENUM alone would still act in the normal manner. Also to correct re-numbering of the command LCTN(...), which doesn't work at present. |
| **POINT** | Pixel detect command, relative to current PAPER colour. Value would generate INK colour. Typical syntax might be:- `IF POINT x,y = RED THEN.....`, where x,y are the current cursor co-ordinates. |
| **SCROLL n** | General command for scrolling, if n=0 then normal kind of scrolling, else "n" determines a number of lines to be scrolled, can be + or -, i.e. two directional scroll, up or down, possibly by means of `<shift arrows>`. |
| **GCHAR** | (Graphic CHARacter mode). Switches LYNX into a 32 column mode, removing "byte boundaries", thus speeding up the screen write routine, making it suitable for faster games to run under BASIC. |
| **ETEXT** | (Enlarged TEXT mode). Switches to 80 column screen, in green only, and implements scroll automatically. Suitable for CP/M. |
| **TERM** | (TERMinal). Initialises a terminal emulation program, so the LYNX can be used as an intelligent graphic (if required) terminal. |
| **ROM n** | Not to be confused with XROM. Selects sideways ROM number "n", to lie between 1-7 for the lower 8K, and 81-87 for the upper 8K. "0" would select normal ROM, from &4000 to &5FFF, defaults to this on switch-on. |
| **PAINT n** | A general fill or paint command which would fill any enclosed area with a defined pattern. "n" would lie between 0-31 (plain colour), and 32-255 patterned paint fills, namely defining a character, setting the ink and paper colours and then "painting" the designated area with the character. |
| **ARC r,s,t** | A drawing routine whereby an arc could be drawn on the screen, r=radius, "s" and "t" define the angle from the vertical position. Positioned by the MOVE command. |
| **SEG n,r,s,t** | Expansion of ARC, to create a segment viz. PIE CHARTS, similar to ARC with n=0 for a line draw, and n=1 for a filled area. Positioned by the MOVE command. |
| **\* ELLIPSE** | This is under review, depending on the best method to adopt. |
| **ON { ERROR } { VARIABLE }** | Standard implementation of the ON command. Related commands would operate automatically. |
| **STRING$ (n),(c)** | Instead of having many spaces in a PRINT line statement, this could be used instead, e.g. STRING$ (10),(32) would place 10 spaces (CHR$(32)) in front of any text. |
| **CHAR (n)** | A character detect command, in addition to the POINT command. "n" would be the ASCII number (32-127) or a defined character (128-255). |
| **XOR ON/OFF** | Based on possibly C.CYTERA's colour routine. Creates beautiful screen displays. |
| **EVAL (string)** | Evaluation of a string e.g. EVAL (A$) = 15 where A$="5\*3". |
| **LOMEM** | Opposite to HIMEM, allows commands like "DPOKE GRAPHIC" to operate in the DATA STORE. Default value is &xxxx, syntax would be; LOMEM-`<number of bytes>`. |
| **BANK (n)** | Bank switch to operate from BASIC, would allow direct writing into video memory, either for graphics or for data storage. "n" to have value from 0-4. |
| **SRESERVE** | A command similar to RESERVE but will operate on the DATA STORE. |
| **CLR** | Or "CLEAR", clears values held in variables, strings, and arrays. |
| **N.....** | New prefix command to the range of MONitor commands. Allows a direct dump to a printer of many of the monitor commands except those requiring entry. |
| **K.....** | New prefix command to the "D" and "R" commands for disk operation. |
| **CONTROL 2** | Allows defining of any ASCII key for functions. |
| **:** | For multistatement lines, this will save memory from line numbering etc. Optional use. |
| **%** | Allows integer variables to be used, which will save memory and speed up mathematical calculations. |
| **MSAVE** | Absent from the ROMs originally, for saving machine code programs from within BASIC. Syntax similar to EXT MSAVE, i.e. MSAVE "FILE NAME",&xxxx,&yyyy,&zzzz. |
| **OLD** | Warm start command. |
| **CURSOR x,y** | To position cursor on screen, extra to the PRINT @ statement. |
| **WIDTH n** | Used with LPRINT command to set number (n) of characters printed across a line. |
| **SEEK (X$,Y$)** | Or INSTR$, searches for X$ within Y$. Ideal for searches used within filer type of program. Returns TRUE or FALSE. |
| **BAUD x,y,z** | For use with the new serial port system, x=receive baud rate, y=transmit baud rate, z=normal or reverse polarity, defaults to x=300, y=300, z=0. The syntax will probably be similar to the TAPE command, but with a selection of 8 different BAUD rates, from 75 to 9600 by software control. There will also be on the SUPER LYNX pcb, a selector switch to change the basic clock rate so that 2 further BAUD rate selections will be possible, namely 150 to 19200 and 300 to 38400. |
| **SIGNAL a,b,c,d** | Sets up conditions for serial communication. "a" sets up number of data bits, "b" sets up parity bits, "c" sets up parity "0" (none), "1" (odd), or "2" (even), and "d" sets up the number of stop bits. Default values are:- a=8, b=0, c=0, d=2. Please note that these values have yet to be finalised. |
| **STATUS** | Tests status of incoming signal. Either "TRUE" or "FALSE". |

## Adjustments to Existing Commands

Certain existing commands and facilities will also be adjusted:-

| Command | Description |
|---|---|
| **LOG (n)** | To correct the "bug" of LOG (1) and LN(1). |

Also the entire printer codes will be available in the vector table, defaulting to ASCII standards wherever possible. This will allow any printer to be run on the LYNX without the need for knowing how to generate "printer patches" from machine code. Also when using a disk drive, it will be possible to "fire up" the DOS after a CALL 0 command. The "EXT" command won't have to be typed, the syntax will automatically search for the command called, although it will appear in listings.

However to implement the above, it is proposed to move the start of BASIC up to &6A00. This will provide approximately a further 170 bytes for new commands and other uses. Although this does reduce the programming area by a small amount, this is compensated for by providing facilities to access any area of RAM (up to 52K) for data or machine code storage. This is regarded as a very small "price" to pay for what is being provided!

These are the proposals to date (1 JUNE 85) of the extensions to BASIC. To implement as many of the proposed commands as possible, it will be necessary to modify the entire set of ROMs. Subject to successful "ROM blowing", no charge would be incurred for replacement of ROMs 1 & 2 with the new facilities. However this would not apply to ROM 3 position as the current ROM is only a 2732 and would have to be replaced with a 2764 (could even be a 27128!). The whole exercise is to improve the programming power of the original LYNX design and this will provide the LYNX owner with three possible options:-

1. To be content with his or her machine and to stay with the original design.
2. To end up with an improved machine with many more features and corrections to the original BASIC.
3. To exchange their machine for the 128K model, which is in many respects incompatible with existing software but does provide many new features. Some of the above changes to the 96K are likely to be implemented in this machine at a later date.

Software is already promised in ROM, eg. an enhanced form of CENTIPEDE and CUB-FORTH with more to follow.

A version of this system will follow for the 128K machine but minus the 80 column facility as the 128K already has this feature. It is to be hoped that with the sideways ROM facility, Digital Research may consider putting their GEM icon system onto the LYNX.

*R B JONES, Prop. PERIPHERAL PRODUCTS.*
