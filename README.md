# circode
Tool for generating circodes. These are simple circular symbols which serve a similar
function to barcodes except a single circode can only encode a single 6-bit value.
Circodes were originally created for attaching to pick-and-place machine nozzles such
that their type could be quickly established by the machine's training camera and
vision processing system.

## Format
![Example Circode](https://github.com/mattbucknall/circode/raw/master/example.png)

A circode consits of 2 black rings (an inner ring and an outer ring). The inner ring's
diameter must be no larger than 67% and no less than 50% of the outer ring's diameter.
The area between the two rings is evenly divided into 20 segments. Black segments are
used to represent '0' bits and white segments are used to represent '1' bits. The 6-bit
value to be encoded is prefixed with seven '0' bits followed by one '1' bit. The value
is suffixed with the ones' complement of itself. Bits are presented in clockwise order
starting (after the preamble) with the encoded value's least significant bit.

## Usage

The script provided in this repository generates a circode with specified parameters and
outputs it as a .png file.

```
circode <output-png> <code> [size] [background]

  <output-png>     Path to output .png file

  <code>           Number to encode (0-63)

  [size]           Diameter of circode in pixels (optional,
                   default = 1024).

  [background]     If 0, background will be transparent, if
                   1, background will be black (optional,
                   default = 0)
```
*Note:* The output includes a cross-hair at the center of the circode. This does not
form part of the circode. It is provided as an alignment aid in case the circode is to
be cutout with a laser cutter (or some other cutting tool).
