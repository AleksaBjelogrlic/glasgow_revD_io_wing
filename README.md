# glasgow_revD_io_wing

Modular test board for Glasgow RevD IO ports. Four of these will connect to a core board to form a complete revD prototype. Doing unconstrained and modular designs will speed up iteration and get us to a finalized design faster.

## Design Goals:

### 1.2V VIO support

- Use 74AXP1T45 level shifters as per [Glasgow #283](https://github.com/GlasgowEmbedded/glasgow/issues/283). 
- No GPIO expander will support this voltage so we have to do something clever for the programmable pulls.
- Pulldowns added on DIR pins as per [Glasgow #552, option 2](https://github.com/GlasgowEmbedded/glasgow/issues/552).
- Option 3 will not work at VIO = 5V as DIR is on the port A side and would be fed with a 3.3V signal, which is lower than the 3.5V threshold for VCCA = 5V.

### Increase VIO output current and support true 5V VIO

- Use a buck-boost regulator, TPS631012 eliminates the need for a DAC as well
- Max 1.5A on each port, can go up to 5.5V regardless of VUSB

### Make the most out of any USB host without browning out

- Adustable current limits on all VIO regulator inputs for 500mA, 1.5A, and 3A capable USB hosts  

### Add a user analog input

- Use the two free pins on each Glasgow port
- Single ended or diff, for voltage and current monitoring on the user's board

### Test new ESD diode array

- [Glasgow #765](https://github.com/GlasgowEmbedded/glasgow/issues/765)

### Improve schematic readablity

- Make the functions of the IO ports as clear as possible from first glance


