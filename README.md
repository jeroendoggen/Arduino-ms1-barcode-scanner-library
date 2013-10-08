# MS1 Barcode scanner library

 - Documentation: http://files.microscan.com/helpfiles/ms1_help_file/index.html

## Solution
 - Arduino library to talk to the device over UART
 - Python library to talk to the device over UART

## Overview of features
### Read cycle:
 - Single mode
 - Multiple mode

### Trigger mode:
 - Trigger the barcode read mode using an external sensor?

### No Read message:
  - might be used to signal an objects has not been detected while other sensors have detected an object (and decide to re-scan the object?)

### Shutter speed:
 - can be changed when the object is moving faster

### Symbologies:
 - 11 different versions --> which ones are important? (select the most popular one in the first implementation)

### Device control:
 - enable /disable device

## Open questions:
 - RTS/CTS: can be enable/disabled
    - default= disabled --> requires less pins)
    - is the datarate ok to avoid buffer overflow at the Arduino side (probably it is)
 - Preamble/postamble character(s) can be configured --> also make it configurable in our own library

## Pseudo code (v1):

    Class BarcodeScanner():
      SetReadingMode() -> continuous, level trigger, serial-data trigger
      SendSerialTrigger()
      ConfigureScanner() -> send various configuration commands
      SelectBarcodeEncoding() -> enable disable the ones you want
      enableReader()
      disableReader()
  
## Pseudo code (v2):

    class symbologies;
    class uart_protocol ;
    class command_interface;
    
    class BarcodeScanner():
      symbologies symb;
      uart_protocol  protocol;
      command_interface command;




