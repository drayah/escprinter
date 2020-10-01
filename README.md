ESCprinter
=======

Simple Java class to allow printing to Epson ESC/P and ESC/P2 matrix printers shared on the network. Currently tested with the Epson LX-300+II 9 pin impact printer but 24 pin support is included.

**Usage**: Printer should be shared on the network. E.g. **\\\computername\printershare**

You use this network path when constructing ESCPrinter objects as follows.

    ESCPrinter p = new ESCPrinter("\\\\computername\\share", false);
    if (p.initialize()) {
        p.setCharacterSet(ESCPrinter.USA);
        p.select15CPI(); //15 characters per inch printing
        p.advanceVertical(5); //go down 5cm
        p.setAbsoluteHorizontalPosition(5); //5cm to the right
        p.bold(true);
        p.print("Let's print some matrix text ;)");
        p.bold(false);
        p.advanceVertical(1);
        p.setAbsoluteHorizontalPosition(5); //back to 5cm
        p.print("Very simple and easy!");
        p.formFeed(); //eject paper
        p.close(); //close stream
    }
    else {
        System.out.println("Couldn't open stream to printer");
    }
** File Closed **
