# Bash OSC
Bash OSC is a basic implementation of the Open Sound Control protocol over UDP written as a Bash script.  The goal is to provide a simple, portable, and performant utility that is not necessarily full-featured (e.g. bundles are not supported).  Care has been taken to minimize dependencies and external calls for both portability as well as performance reasons.  Bash OSC is open-source and free to use, modify, and distribute according to the BSD 3-Clause License.

## Usage
Bash OSC can be used either as a sourced library or as a stand-alone command-line utility.  Either way, you will need to set the variables ``OSC_IP`` and ``OSC_PORT`` before using Bash OSC:

```bash
export OSC_IP=169.254.246.252
export OSC_PORT=10023
```

### From the Command-Line
Be sure to set the IP and port as mentioned above.

**Usage:** osc *address* *type_tags* *argument_1* [*argument_2*...]

|                      |                                            |
|----------------------|--------------------------------------------|
| **address**          | The OSC address string (e.g. /path/method) |
| **type_tags** &nbsp; | Character(s) indicating the types of *argument* in order <ul><li>``'s'`` for string</li><li>``'i'`` for integer</li><li>``'f'`` for float</li></ul> |
| **argument**         | Argument(s) corresponding to the types defined by *type_tags*<br>**Note: float arguments must be specified in hexidecimal** |

**Examples**

Sends an OSC message with a single string to set the name of channel 29

```bash
osc /ch/29/config/name s "Bass Amp"
```

Sends an OSC message with a single float to set the DCA 4 fader level

```bash
osc /dca/4/fader f 3f400000
```

Sends an OSC message with two strings, an integer, and a float argument

```bash
osc /channel/75/config ssif "Cello 5" ON 13 00000000
```


### As a Library

```bash
source ~/bin/osc
OSC_IP=169.254.246.252
OSC_PORT=10023
```
