LavishScript API Specification (LavishScript)
LavishScript base API
---
# Events
## Event: Alias Added

## Event: Alias Removed

## Event: Command Added

## Event: Command Removed

## Event: Object Type Added

## Event: Object Type Removed

## Event: Top-Level Object Added

## Event: Top-Level Object Removed

## Event: Fatal Error

## Event: Data Sequence Error


---
# Commands
## Command: Test

## Command: Commands

## Command: Alias

## Command: LSVersion

## Command: Redirect

## Command: DeclareVariable
### Syntax
* `DeclareVariable` < [<[string](#Type:%20string) `varName`>|<[string](#Type:%20string) `varName[... uint arrayExtents]`>]> [[string](#Type:%20string) `typeName`="string"] "globalkeep"|"global"|"script"|"object"|"local" <[string](#Type:%20string) `initialValue`>

## Command: DeleteVariable
### Syntax
* `DeleteVariable` <[string](#Type:%20string) `varName`>

## Command: RunScript
### Syntax
* `RunScript` <[string](#Type:%20string) `filename`> [... [string](#Type:%20string) `scriptParams`]

## Command: EndScript
### Syntax
* `EndScript` <[string](#Type:%20string) `filename`>
* `EndScript` "*"

## Command: Execute

## Command: Return
### Syntax
* `Return` [... [string](#Type:%20string) `returnObjectInitParams`]

## Command: Call
### Syntax
* `Call` <[string](#Type:%20string) `functionName`> [... [string](#Type:%20string) `functionParams`]

## Command: Wait
### Syntax
* `Wait` < [<[uint](#Type:%20uint) `deciseconds`>|"-s" <[float](#Type:%20float) `seconds`>]> [[bool](#Type:%20bool) `pauseUntilExpression`]

## Command: WaitScript
### Syntax
* `WaitScript` <[string](#Type:%20string) `filename`> <... [string](#Type:%20string) `scriptParams`>

## Command: Arg

## Command: WaitFrame
### Syntax
* `WaitFrame`

## Command: Scripts
### Syntax
* `Scripts` "-running"|"-available"

## Command: LSType
### Syntax
* `LSType` "-list"
* `LSType` <[string](#Type:%20string)>

## Command: TopLevelObject
### Syntax
* `TopLevelObject`

## Command: TimedCommand

## Command: QueueCommand
### Syntax
* `QueueCommand` <... [string](#Type:%20string) `command`>

## Command: ExecuteQueued
### Syntax
* `ExecuteQueued` [[string](#Type:%20string) `needle`]

## Command: FlushQueued
### Syntax
* `FlushQueued` [[string](#Type:%20string) `needle`]

## Command: NoOp

## Command: Turbo
### Syntax
* `Turbo` [[uint](#Type:%20uint) `maxCommandsPerPulse`=150]

## Command: Processor

## Command: ExecuteAtom

## Command: AddAtom

## Command: DeleteAtom

## Command: Squelch
### Syntax
* `Squelch` <... [string](#Type:%20string) `command`>

## Command: Echo
### Syntax
* `Echo` <... [string](#Type:%20string) `text`>

## Command: AddTrigger
### Syntax
* `AddTrigger` <[string](#Type:%20string) `functionName`> <[string](#Type:%20string) `needle`>

## Command: RemoveTrigger
### Syntax
* `RemoveTrigger` <[string](#Type:%20string) `functionName`>

## Command: WaitFor
### Syntax
* `WaitFor` <... [string](#Type:%20string) `upTo20needles`> [[uint](#Type:%20uint) `maxWaitDeciseconds`]


---
# Top-Level Objects
## TLO: Type
- [type](#Type:%20type) `Type[` [string](#Type:%20string) `typeName` `]`

## TLO: Int
- [int](#Type:%20int) `Int[` [int](#Type:%20int) `value` `]`

## TLO: Int64
- [int64](#Type:%20int64) `Int64[` [int64](#Type:%20int64) `value` `]`

## TLO: String
- [string](#Type:%20string) `String[` [string](#Type:%20string) `value` `]`

## TLO: Float
- [int](#Type:%20int) `Float[` [int](#Type:%20int) `value` `]`

## TLO: Bool
- [bool](#Type:%20bool) `Bool[` [bool](#Type:%20bool) `value` `]`

## TLO: If
- [string](#Type:%20string) `If[` [float64](#Type:%20float64) `condition` `,` [string](#Type:%20string) `trueValue` `,` <[string](#Type:%20string) `falseValue`=""> `]`: If `condition` is non-zero, results in `trueValue`, otherwise `falseValue`

## TLO: Time
- [time](#Type:%20time) `Time`: The current local date/time

## TLO: Enum
- [enumtype](#Type:%20enumtype) `Enum[` [string](#Type:%20string) `enumName` `]`

## TLO: ForEach
- [keyvaluepair](#Type:%20keyvaluepair) `ForEach`: Current Key,Value in a currently-executing ForEach

## TLO: Return
- [object](#Type:%20object) `Return`: The returned value from the last Call, from the current script

## TLO: Returning
- [object](#Type:%20object) `Returning`: The instantiated object to be returned from the current function/member

## TLO: Variable
- [object](#Type:%20object) `Variable[` [string](#Type:%20string) `descriptor` `]`

## TLO: QueuedCommands
- [bool](#Type:%20bool) `QueuedCommands`: TRUE if commands are currently queued for the current script
- [bool](#Type:%20bool) `QueuedCommands[` [string](#Type:%20string) `commandSubstring` `]`: TRUE if commands containing the `commandSubstring` are currently queued for the current script

## TLO: Arg
- [string](#Type:%20string) `Arg[` [uint](#Type:%20uint) `numArg` `,` ... [string](#Type:%20string) `args` `]`

## TLO: Script
- [script](#Type:%20script) `Script`: Currently executing script, if any
- [script](#Type:%20script) `Script[` [string](#Type:%20string) `scriptFile` `]`

## TLO: Function
- [function](#Type:%20function) `Function`: Currently executing function, from the current Script, if any

## TLO: Execute
- [int](#Type:%20int) `Execute[` [string](#Type:%20string) `command` `]`

## TLO: Select
- [int](#Type:%20int) `Select[` [string](#Type:%20string) `needle` `,` ... [string](#Type:%20string) `haystack` `]`: Finds the index of a value within `haystack` matching `needle`

## TLO: This
- [weakref](#Type:%20weakref) `This`
- [weakref](#Type:%20weakref) `This[` "parent" `]`

## TLO: Event
- [event](#Type:%20event) `Event[` [uint](#Type:%20uint) `eventID` `]`
- [event](#Type:%20event) `Event[` [string](#Type:%20string) `eventName` `]`

## TLO: WaitFor
- [int](#Type:%20int) `WaitFor`: The last WaitFor result, from the currently executing script

## TLO: VariableScope
- [variablescope](#Type:%20variablescope) `VariableScope`: The current local Variable Scope for the currently executing script if there is one, otherwise the global Variable Scope

## TLO: PersistentObject
- [weakref](#Type:%20weakref) `PersistentObject[` [uint](#Type:%20uint) `handle` `]`

## TLO: Query
- [bool](#Type:%20bool) `Query[` [object](#Type:%20object) `obj` `,` [string](#Type:%20string) `expression` `]`

## TLO: LMAC
- [lavishmachine](#Type:%20lavishmachine) `LMAC`

## TLO: Math
- [math](#Type:%20math) `Math`

## TLO: System
- [system](#Type:%20system) `System`

## TLO: LavishScript
- [lavishscript](#Type:%20lavishscript) `LavishScript`


---
# Types
## Type: int
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Initializers
- `int[` [int](#Type:%20int) `value` `]`


### Members
- [float](#Type:%20float) `Float`: This number, converted to a float
- [string](#Type:%20string) `Hex`: A hexadecimal string equivalent to this number
- [string](#Type:%20string) `LeadingZeroes[` [uint](#Type:%20uint) `digits` `]`: A string representation of this number, with at least this many decimal places.  The number will be lead with zeroes to reach the desired length
- [int](#Type:%20int) `Reverse`: This number, with its bytes reversed (1234 is turned into 3523477504.. easier to see in hex: 00 00 04 D2 -> D2 04 00 00)
- [bool](#Type:%20bool) `Between[` [int](#Type:%20int) `,` [int](#Type:%20int) `]`: TRUE if   a&lt;= value and value &lt;= b
- [uint](#Type:%20uint) `Unsigned`: This number as 32-bit unsigned
- [bool](#Type:%20bool) `Equal[` [int](#Type:%20int) `expression` `]`: TRUE if the int matches the specified value
- [string](#Type:%20string) `AsJSON`: A string with the value of the int, as would be in JSON

### Methods
- `Reverse`
- `Inc[` <[int](#Type:%20int) `expression`=1> `]`: Increments this int by a given amount
- `Inc`: Increments this int by 1
- `Dec[` <[int](#Type:%20int) `expression`=1> `]`: Decrements this int by a given amount
- `Dec`: Decrements this int by 1
- `Set[` [int](#Type:%20int) `expression` `]`: Sets this int to a given value



## Type: uint
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Initializers
- `uint[` [uint](#Type:%20uint) `value` `]`


### Members
- [float](#Type:%20float) `Float`: This number, converted to a float
- [string](#Type:%20string) `Hex`: A hexadecimal string equivalent to this number
- [string](#Type:%20string) `LeadingZeroes[` `#` `]`: A string representation of this number, with at least this many decimal places.  The number will be lead with zeroes to reach the desired length
- [uint](#Type:%20uint) `Reverse`: This number, with its bytes reversed (1234 is turned into 3523477504.. easier to see in hex: 00 00 04 D2 -> D2 04 00 00)
- [bool](#Type:%20bool) `Between[` [int](#Type:%20int) `,` [int](#Type:%20int) `]`: TRUE if   a&lt;= value and value &lt;= b
- [int](#Type:%20int) `Signed`: This number as 32-bit signed
- [bool](#Type:%20bool) `Equal[` [formula](#Type:%20formula) `]`: TRUE if the uint matches the specified value
- [string](#Type:%20string) `AsJSON`: A string with the value of the uint, as would be in JSON

### Methods
- `Reverse[`???`]`
- `Inc[` <[uint](#Type:%20uint) `expression`=1> `]`: Increments this uint by a given amount
- `Inc`: Increments this uint by 1
- `Dec[` <[uint](#Type:%20uint) `expression`=1> `]`: Decrements this uint by a given amount
- `Dec`: Decrements this uint by 1
- `Set[` [formula](#Type:%20formula) `]`: Sets this uint to a given value



## Type: string
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Indexers
- [byte](#Type:%20byte) `string[` [uint](#Type:%20uint) `position` `]`

### Members
- [string](#Type:%20string) `Mid[` [uint](#Type:%20uint) `position` `,` [uint](#Type:%20uint) `length` `]`: Returns a string containing the given length at the given position (1-based) of the original string
- [string](#Type:%20string) `Left[` [int](#Type:%20int) `length` `]`: Returns a string containing the leftmost # characters of the original string. A negative number can be used to give the leftmost (Length-#)
- [string](#Type:%20string) `Right[` [int](#Type:%20int) `length` `]`: Returns a string containing the rightmost # characters of the original string. A negative number can be used to give the rightmost (Length-#)
- [int64](#Type:%20int64) `Find[` [string](#Type:%20string) `needle` `]`: Returns the 1-based position of a given substring in the original string, or NULL
- [int64](#Type:%20int64) `Length`: Returns the length of the string
- [string](#Type:%20string) `Upper`: Returns a string containing the original string in all upper case
- [string](#Type:%20string) `Lower`: Returns a string containing the original string in all lower case
- [int](#Type:%20int) `Compare[` [string](#Type:%20string) `compareTo` `]`: Compares this string, without regards to case, to the given text. Return value is less than 0 if the text would come before it in the dictionary, 0 if it is equal, or greater than 0 if the text would come after the string
- [int](#Type:%20int) `CompareCS[` [string](#Type:%20string) `compareTo` `]`: Compares this string, with regards to case, to the given text. Return value is less than 0 if the text would come before it in the dictionary, 0 if it is equal, or greater than 0 if the text would come after the string
- [bool](#Type:%20bool) `Equal[` [string](#Type:%20string) `compareTo` `]`: TRUE if the string is equal to, without regards to case, the given text
- [bool](#Type:%20bool) `NotEqual[` [string](#Type:%20string) `compareTo` `]`: TRUE if the string is not equal to, without regards to case, the given text
- [bool](#Type:%20bool) `EqualCS[` [string](#Type:%20string) `compareTo` `]`: TRUE if the string is equal to, with regards to case, the given text
- [bool](#Type:%20bool) `NotEqualCS[` [string](#Type:%20string) `compareTo` `]`: TRUE if the string is not equal to, with regards to case, the given text
- [bool](#Type:%20bool) `Equals[` [string](#Type:%20string) `compareTo` `]`
- [bool](#Type:%20bool) `NotEquals[` [string](#Type:%20string) `compareTo` `]`
- [bool](#Type:%20bool) `EqualsCS[` [string](#Type:%20string) `compareTo` `]`
- [bool](#Type:%20bool) `NotEqualsCS[` [string](#Type:%20string) `compareTo` `]`
- [int](#Type:%20int) `Count[` [string](#Type:%20string) `findCharacter` `]`: The number of times a specific character appears in the string
- [string](#Type:%20string) `Token[` [string](#Type:%20string) `token` `,` [uint](#Type:%20uint) `numToken` `]`: "Tokenizes" the string by the given separator and returns the #th token
- [string](#Type:%20string) `EscapeQuotes`: Uses slashes to escape " only
- [string](#Type:%20string) `Escape[` <[uint](#Type:%20uint) `mode`=1> `]`: If escapeLavishScript is false/0, Uses slashes to escape \, ", carriage return, line feed, tab, but NOT LavishScript data sequences
- [string](#Type:%20string) `Escape`: Uses slashes to escape \, ", carriage return, line feed, tab, as well as LavishScript data sequences
- [string](#Type:%20string) `Replace[` `character` `,` `with` `,` ... [string](#Type:%20string) `]`: Performs single-character replacement with any number of character pairs
- [byte](#Type:%20byte) `GetAt[` [uint](#Type:%20uint) `position` `]`: Retrieves a character at the #th position in the string (1-based)
- [unistring](#Type:%20unistring) `UniString`
- [string](#Type:%20string) `URLEncode`: Returns a %u encoded version of the string, suitable for urls
- [bool](#Type:%20bool) `NotNULLOrEmpty`: TRUE if the string is not empty and does not contain the literal NULL. This provides a shortcut for: &lt;tt>if ${MyString.Length} &amp;&amp; !${MyString.Equals[NULL]}&lt;/tt>
- [string](#Type:%20string) `AsJSON`: Returns a JSON encoded version of the string, including surrounding quotes
- [string](#Type:%20string) `Trim`: Returns a copy of the string with no leading or trailing whitespace
- [string](#Type:%20string) `ReplaceSubstring[` [string](#Type:%20string) `needle` `]`
- [string](#Type:%20string) `ReplaceSubstring[` [string](#Type:%20string) `haystack` `]`
- [string](#Type:%20string) `ReplaceSubstring[` `needle` `,` `replacement` `]`: Performs in-place replacement of a needle in a haystack. For example, &lt;tt>${String[abcdefg].ReplaceSubstring[def,xyz]}&lt;/tt> is &lt;tt>abcxyzg&lt;/tt>
- [string](#Type:%20string) `StartsWith`
- [string](#Type:%20string) `EndsWith`

### Methods
none.


## Type: rgb
- Persistent: No ([weakref](#Type:%20weakref) not supported)

As Text: Same as `Hex`

### Members
- [byte](#Type:%20byte) `Red`: 0-255 indicating the amount of red
- [byte](#Type:%20byte) `Green`: 0-255 indicating the amount of green
- [byte](#Type:%20byte) `Blue`: 0-255 indicating the amount of blue
- [string](#Type:%20string) `Hex`: A hexadecimal value representing the color, in the form rrggbb.  For example, "ff0000" is full red.

### Methods
- `Set[` [string](#Type:%20string) `hexValue` `]`
- `Set`: Sets the rgb hex to a given value



## Type: byte
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Initializers
- `byte[` [byte](#Type:%20byte) `value` `]`

### Members
- [bool](#Type:%20bool) `Between[` [byte](#Type:%20byte) `,` [byte](#Type:%20byte) `]`
- ??? `Equal[`???`]`

### Methods
- `Inc[` <[byte](#Type:%20byte) `expression`=1> `]`: Increments this byte by a given amount
- `Inc`: Increments this byte by 1
- `Dec[` <[byte](#Type:%20byte) `expression`=1> `]`: Decrements this byte by a given amount
- `Dec`: Decrements this bye by 1
- `Set[` [byte](#Type:%20byte) `expression` `]`: Sets this bye to a given value



## Type: bool
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Initializers
- `bool[` [bool](#Type:%20bool) `value` `]`

As Text: TRUE (non-zero) or FALSE (zero)

### Members
- [bool](#Type:%20bool) `Equal[` [bool](#Type:%20bool) `expression` `]`: TRUE if the boolean value matches the boolean result of the calculation (zero is FALSE, non-zero is TRUE)
- [bool](#Type:%20bool) `Not`: Gives the opposite value, e.g. if the value is TRUE, Not is FALSE
- [string](#Type:%20string) `AsJSON`: A string containing true or false as would be specified in JSON

### Methods
- `Toggle`: Toggles between TRUE and FALSE
- `Set[` [bool](#Type:%20bool) `expression` `]`: Sets this bool to a specific value



## Type: unistring
- Base Type: [string](#Type:%20string)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- [string](#Type:%20string) `String`

### Methods
none.


## Type: mutablestring
- Base Type: [string](#Type:%20string)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Initializers
- `mutablestring[` [string](#Type:%20string) `value` `]`

### Members
- [string](#Type:%20string) `String`: Retrieves the appropriate string object from this mutablestring

### Methods
- `Set`
- `Set[` [string](#Type:%20string) `newValue` `]`: Sets the value of the string to this new text
- `Concat[` [string](#Type:%20string) `value` `]`: Concatenates the string with this new text
- `ToUpper`: Converts the string to upper case
- `ToLower`: Converts the string to lower case
- `Prepend[` [string](#Type:%20string) `value` `]`



## Type: float
- Persistent: No ([weakref](#Type:%20weakref) not supported)


### Members
- [string](#Type:%20string) `Deci`: The value of this float, to the nearest tenth
- [string](#Type:%20string) `Centi`: The value of this float, to the nearest hundredth
- [string](#Type:%20string) `Milli`: The value of this float, to the nearest thousandth
- [int64](#Type:%20int64) `Int`: The value of this float, to its largest whole number (e.g. for 1.9 this is 1, for -0.1, this is -1)
- [string](#Type:%20string) `Precision[` [int](#Type:%20int) `numPlaces` `]`: The value of this float, to the nearest # decimal places (e.g. 1 is tenths, 2 is hundredths, 3 is thousandths, and so on)
- [int64](#Type:%20int64) `Ceil`: The value of this float, to its largest partial number (e.g. for 1.1 this is 2, for -0.1 this is 0).
- [int](#Type:%20int) `Round`: The value of this float, rounded to the nearest whole number
- [bool](#Type:%20bool) `Equal[` [float](#Type:%20float) `expression` `]`: TRUE if the float matches the specified value
- [string](#Type:%20string) `AsJSON`: A string with the value of the float, as would be in JSON
- [bool](#Type:%20bool) `Between[` [float](#Type:%20float) `minInclusive` `,` [float](#Type:%20float) `maxInclusive` `]`: TRUE if   a&lt;= value and value &lt;= b

### Methods
- `Inc[` <[float](#Type:%20float) `expression`=1.0> `]`: Increments this float by a given amount
- `Inc`: Increments this float by 1.0
- `Dec[` <[float](#Type:%20float) `expression`=1.0> `]`: Decrements this float by a given amount
- `Dec`: Decrements this float by 1.0
- `Set[` [float](#Type:%20float) `expression` `]`: Sets this float to a given value



## Type: int64
- Persistent: No ([weakref](#Type:%20weakref) not supported)


### Members
- [float](#Type:%20float) `Float`: This number, converted to a float (NOTE: Float is only accurate to 32 bits of precision)
- [string](#Type:%20string) `Hex`: A hexadecimal string equivalent to this number
- [string](#Type:%20string) `LeadingZeroes[` `#` `]`: A string representation of this number, with at least this many decimal places.  The number will be lead with zeroes to reach the desired length
- [bool](#Type:%20bool) `Between[` [int64](#Type:%20int64) `,` [int64](#Type:%20int64) `]`: TRUE if   a&lt;= value and value &lt;= b
- [bool](#Type:%20bool) `Equal[` [formula](#Type:%20formula) `]`: TRUE if the int64 matches the specified value
- [string](#Type:%20string) `AsJSON`: A string with the value of the int64, as would be in JSON

### Methods
- `Inc[` <[int64](#Type:%20int64) `expression`=1> `]`: Increments this int64 by a given amount
- `Inc`: Increments this int64 by 1
- `Dec[` <[int64](#Type:%20int64) `expression`=1> `]`: Decrements this int64 by a given amount
- `Dec`: Decrements this int64 by 1
- `Set[` [int64](#Type:%20int64) `expression` `]`: Sets this int64 to a given value



## Type: float64
- Persistent: No ([weakref](#Type:%20weakref) not supported)


### Members
- [string](#Type:%20string) `Deci`: The value of this float, to the nearest tenth
- [string](#Type:%20string) `Centi`: The value of this float, to the nearest hundredth
- [string](#Type:%20string) `Milli`: The value of this float, to the nearest thousandth
- [int64](#Type:%20int64) `Int`: The value of this float, to its largest whole number (e.g. for 1.9 this is 1, for -0.1, this is -1)
- [string](#Type:%20string) `Precision[` [int](#Type:%20int) `numPlaces` `]`: The value of this float, to the nearest # decimal places (e.g. 1 is tenths, 2 is hundredths, 3 is thousandths, and so on)
- [int64](#Type:%20int64) `Ceil`: The value of this float, to its largest partial number (e.g. for 1.1 this is 2, for -0.1 this is 0).
- [int](#Type:%20int) `Round`: The value of this float, rounded to the nearest whole number
- [bool](#Type:%20bool) `Equal[` [float](#Type:%20float) `expression` `]`: TRUE if the float64 matches the specified value
- [string](#Type:%20string) `AsJSON`: A string with the value of the float64, as would be in JSON
- [bool](#Type:%20bool) `Between[` [float64](#Type:%20float64) `minInclusive` `,` [float64](#Type:%20float64) `maxInclusive` `]`: TRUE if   a&lt;= value and value &lt;= b

### Methods
- `Inc[` <[float64](#Type:%20float64) `expression`=1> `]`: Increments this float64 by a given amount
- `Inc`: Increments this float64 by 1.0
- `Dec[` <[float64](#Type:%20float64) `expression`=1> `]`: Decrements this float64 by a given amount
- `Dec`: Decrements this float64 by 1.0
- `Set[` [float64](#Type:%20float64) `expression` `]`: Sets this float64 to a given value



## Type: floatptr
- Base Type: [float](#Type:%20float)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: float64ptr
- Persistent: No ([weakref](#Type:%20weakref) not supported)


### Members
- ??? `Deci[`???`]`
- ??? `Centi[`???`]`
- ??? `Milli[`???`]`
- ??? `Int[`???`]`
- ??? `Precision[`???`]`
- ??? `Ceil[`???`]`
- ??? `Round[`???`]`
- ??? `Equal[`???`]`
- ??? `AsJSON[`???`]`

### Methods
- `Inc[`???`]`
- `Dec[`???`]`
- `Set[`???`]`



## Type: stringptr
- Base Type: [string](#Type:%20string)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: uintptr
- Base Type: [uint](#Type:%20uint)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: intptr
- Base Type: [int](#Type:%20int)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: int64ptr
- Persistent: No ([weakref](#Type:%20weakref) not supported)


### Members
- ??? `Float[`???`]`
- ??? `Hex[`???`]`
- ??? `LeadingZeroes[`???`]`
- ??? `Address[`???`]`
- ??? `Equal[`???`]`
- ??? `AsJSON[`???`]`

### Methods
- `Inc[`???`]`
- `Dec[`???`]`
- `Set[`???`]`



## Type: rgbptr
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: byteptr
- Base Type: [byte](#Type:%20byte)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: boolptr
- Base Type: [bool](#Type:%20bool)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: math

### Members
- [float](#Type:%20float) `Abs[` [float](#Type:%20float) `value` `]`: Returns the absolute value of a given formula
- [uint](#Type:%20uint) `Rand[` [uint](#Type:%20uint) `range` `]`: Returns a random number from 0 to # - 1, where # is the result of the given formula. The maximum value that can be returned is 32767.
- [float64](#Type:%20float64) `Calc[` [float64](#Type:%20float64) `expression` `]`: Returns the result of a given formula
- [float](#Type:%20float) `Sin[` [float64](#Type:%20float64) `expression` `]`: Returns the sine of a given formula in degrees
- [float](#Type:%20float) `Cos[` [float64](#Type:%20float64) `expression` `]`: Returns the cosine of a given formula in degrees
- [float](#Type:%20float) `Tan[` [float64](#Type:%20float64) `expression` `]`: Returns the tangent of a given formula in degrees
- [float](#Type:%20float) `Asin[` [float64](#Type:%20float64) `expression` `]`: Returns the asin of a given formula in degrees (&lt;tt>asin(sin(x))=x&lt;/tt>)
- [float](#Type:%20float) `Acos[` [float64](#Type:%20float64) `expression` `]`: Returns the acos of a given formula in degrees (&lt;tt>acos(cos(x))=x&lt;/tt>)
- [float](#Type:%20float) `Atan[` [float64](#Type:%20float64) `expression` `]`: Returns the atan of a given formula in degrees (&lt;tt>atan(tan(x))=x&lt;/tt>)
- [float](#Type:%20float) `Atan[` [float64](#Type:%20float64) `expression1` `,` [float64](#Type:%20float64) `expression2` `]`: Returns the atan2 of two given formulae in degrees
- [string](#Type:%20string) `Hex[` [int](#Type:%20int) `value` `]`: Returns a hexadecimal string equivalent to the #
- [int](#Type:%20int) `Dec[` [string](#Type:%20string) `hexValue` `]`: Returns the decimal equivalent to the hexadecimal value given
- [int](#Type:%20int) `Not[` [int](#Type:%20int) `value` `]`: Returns the bitwise NOT of the #
- [float](#Type:%20float) `Distance[` [float](#Type:%20float) `X1` `,` [float](#Type:%20float) `X2` `]`: Returns the 1-dimensional distance between x1 and x2
- [float](#Type:%20float) `Distance[` [float](#Type:%20float) `X1` `,` [float](#Type:%20float) `Y1` `,` [float](#Type:%20float) `X2` `,` [float](#Type:%20float) `Y2` `]`: Returns the 2-dimensional distance between x1,y1 and x2,y2
- [float](#Type:%20float) `Distance[` [float](#Type:%20float) `X1` `,` [float](#Type:%20float) `Y1` `,` [float](#Type:%20float) `Z1` `,` [float](#Type:%20float) `X2` `,` [float](#Type:%20float) `Y2` `,` [float](#Type:%20float) `Z2` `]`: Returns the 3-dimensional distance between x1,y1,z1 and x2,y2,z2
- [float](#Type:%20float) `Sqrt[` [float64](#Type:%20float64) `expression` `]`: Returns the square root of a given formula
- [int64](#Type:%20int64) `Calc64[` [int64](#Type:%20int64) `expression` `]`: Returns the result of a given formula with 64-bit integer precision
- [float](#Type:%20float) `DistancePointLine[` [float](#Type:%20float) `pointX` `,` [float](#Type:%20float) `pointY` `,` [float](#Type:%20float) `segmentStartX` `,` [float](#Type:%20float) `segmentStartY` `,` [float](#Type:%20float) `segmentEndX` `,` [float](#Type:%20float) `segmentEndY` `]`: Returns the distance from x,y to the nearest point on the line from a and b, or NULL if the perpendicular passing through point (x,y) to the line defined by (ax,ay) (bx,by) does not intersect on the segment between points a and b.
- [float](#Type:%20float) `Log[` [float64](#Type:%20float64) `expression` `]`

### Methods
none.


## Type: type
- Persistent: No ([weakref](#Type:%20weakref) not supported)

As Text: Same as `Name`

### Members
- [string](#Type:%20string) `Name`: Name of the data type
- [string](#Type:%20string) `TypeMember[` [uint](#Type:%20uint) `id` `]`
- [uint](#Type:%20uint) `TypeMember[` [string](#Type:%20string) `name` `]`
- [string](#Type:%20string) `PersistentClass`
- [jsonobject](#Type:%20jsonobject) `Metadata`

### Methods
none.


## Type: time
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Initializers
- `time[` [int](#Type:%20int) `timestamp` `]`

As Text: Same as `Time24`

### Members
- [intptr](#Type:%20intptr) `Hour`: Hour of the day (0-23)
- [intptr](#Type:%20intptr) `Minute`: Minute of the hour (0-59)
- [intptr](#Type:%20intptr) `Second`: Second of the minute (0-59)
- [uint](#Type:%20uint) `DayOfWeek`: Day of the week (1-7)
- [intptr](#Type:%20intptr) `Day`: Day of the month (1-31 depending on the month)
- [uint](#Type:%20uint) `Month`: Month of the year (1-12)
- [uint](#Type:%20uint) `Year`: Year
- [string](#Type:%20string) `Time12`: Time in hh:mm:ss given in 12-hour format
- [string](#Type:%20string) `Time24`: Time in hh:mm:ss given in 24-hour format
- [string](#Type:%20string) `Date`: Date in mm/dd/yyyy
- [bool](#Type:%20bool) `Night`: TRUE if current time is after 7pm and before 7am
- [uint](#Type:%20uint) `SecondsSinceMidnight`: Number of seconds since midnight
- [uint](#Type:%20uint) `Timestamp`: Number of seconds since epoch (standard UNIX timestamp)
- [intptr](#Type:%20intptr) `DayOfWeekPtr`: Day of the week (0-6) - Mainly useful for *setting*
- [intptr](#Type:%20intptr) `MonthPtr`: Month of the year (0-11) - Mainly useful for *setting*
- [intptr](#Type:%20intptr) `YearPtr`: Year-1900 (e.g. 0 is 1900, 100 is 2000) - Mainly useful for *setting*

### Methods
- `Set[` [int](#Type:%20int) `timestamp` `]`: Sets the value based on the given timestamp (standard UNIX timestamp, number of seconds since epoch)
- `Update`: Updates the type after setting an individual member (NOT needed when using the Set method)



## Type: array
- Base Type: [objectcontainer](#Type:%20objectcontainer)
- Persistent: No ([weakref](#Type:%20weakref) not supported)


### Members
- [uint](#Type:%20uint) `Dimensions`: Total number of extents of the array (e.g. 2-dimensional has two extents)
- [uint](#Type:%20uint) `Size[` <[uint](#Type:%20uint) `numDimension`> `]`: Total number of elements in a given dimension of the array
- [uint](#Type:%20uint) `Size`: Total number of elements in the array, including all dimensions
- [mutablestring](#Type:%20mutablestring) `Expand`
- [mutablestring](#Type:%20mutablestring) `Expand[` [begin](#Type:%20begin) `#` `,` `length` `]`: Retrieves the text representation of each object in the array as quoted parameters, separated by spaces.  If no parameters are given to Expand, the entire array will be used.  If only the begin # is used, the rest of the array, beginning with the element # specified, will be used.  If the length is additionally given, that number of elements from the array will be used, beginning with the element # specified as the beginning.
- [mutablestring](#Type:%20mutablestring) `ExpandComma`
- [mutablestring](#Type:%20mutablestring) `ExpandComma[` [begin](#Type:%20begin) `#` `,` `length` `]`: Retrieves the text representation of each object in the array as quoted parameters, separated by commas.  If no parameters are given to Expand, the entire array will be used.  If only the begin # is used, the rest of the array, beginning with the element # specified, will be used.  If the length is additionally given, that number of elements from the array will be used, beginning with the element # specified as the beginning.
- [unistring](#Type:%20unistring) `AsJSON[` <"multiline"> `]`
- [unistring](#Type:%20unistring) `AsJSON`: Returns a JSON array representation of this array, with each element converted by using its AsJSON member

### Methods
- `ForEach[` [string](#Type:%20string) `command` `]`: For each element in the array, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration



## Type: system
- Persistent: No ([weakref](#Type:%20weakref) not supported)


### Members
- [string](#Type:%20string) `OS`: Operating system identifier (e.g. Microsoft Windows XP)
- [uint](#Type:%20uint) `MemFree`: Amount of free physical system RAM, in megabytes
- [uint](#Type:%20uint) `MemTotal`: Total amount of physical system RAM, in megabytes
- [string](#Type:%20string) `OSBuild`: Operating system build identifier (e.g. 2600.xpsp_sp2_rtm040803-2158)
- [uint](#Type:%20uint) `GetProcAddress[` `module` `,` `function` `]`: Retrieves the address of an exported function, usually in a DLL. (Level of understanding: High)
- [uint](#Type:%20uint) `TickCount`: A timestamp given in milliseconds.  This value does "wrap" every 46 days or so.
- ??? `GetCurrentDirectory[`???`]`
- [uint](#Type:%20uint) `MemoryUsage`: Amount of memory used by this process (the uplink or session), in bytes
- ??? `Processors[`???`]`
- ??? `ClipboardText[`???`]`
- ??? `ProcessID[`???`]`
- [string](#Type:%20string) `RegistryValue[` `hklm/hkcu` `,` `key` `,` `value` `]`: Retrieve a REG_DWORD, REG_SZ, or REG_EXPAND_SZ value from the system registry

### Methods
- `SetClipboardText[`???`]`



## Type: point3f
- Persistent: No ([weakref](#Type:%20weakref) not supported)



### Members
- [floatptr](#Type:%20floatptr) `X`: X coordinate
- [floatptr](#Type:%20floatptr) `Y`: Y coordinate
- [floatptr](#Type:%20floatptr) `Z`: Z coordinate
- [string](#Type:%20string) `XYZ`: concatenated XYZ string, separated by commas
- [string](#Type:%20string) `XYZ[` `#` `]`: concatenated XYZ string, separated by given field separator character
- ??? `Adjust[`???`]`
- ??? `Distance[`???`]`
- ??? `DistancePointLine[`???`]`

### Methods
- `Set[` `X` `]`: Sets x to a given value
- `Set[` `X` `,` `Y` `]`: Sets x,y to a given value
- `Set[` `X` `,` `Y` `,` `Z` `]`: Sets x,y,z to a given value
- `Adjust[`???`]`



## Type: lavishscript
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- [string](#Type:%20string) `Version`: LavishScript version number (e.g. 1.07)
- [filepath](#Type:%20filepath) `CurrentDirectory`: Current directory according to LavishScript
- [int](#Type:%20int) `RunningTime`: Amount of time, in milliseconds, the current application has been running.  This value wraps after about 23 days of leaving the application running.
- [filepath](#Type:%20filepath) `HomeDirectory`: Home directory according to LavishScript
- [string](#Type:%20string) `LSModule`: LavishScript version number
- [string](#Type:%20string) `ExecuteAtom[` `name` `,` ... [string](#Type:%20string) `]`: Executes an atom with the given name in global- or script-scope (if a script is currently in context).  Extra parameters are passed as parameters to the atom.  If the atom returns a value, this will be the string given.
- [filepath](#Type:%20filepath) `Executable`: Executable filename for the current process
- ??? `CommandLine[`???`]`
- [variablescope](#Type:%20variablescope) `VariableScope`: The global variable scope
- [uint](#Type:%20uint) `CreateQuery[` `expression` `]`: ([[LavishScript:Object Queries|Object Queries]]) Creates a query with the given expression -- e.g. ${LavishScript.CreateQuery[Name=="Bonkers"]}
- [string](#Type:%20string) `RetrieveQueryExpression[` `#` `]`: ([[LavishScript:Object Queries|Object Queries]]) Retrieves the query expression for a previously created query, by ID
- [bool](#Type:%20bool) `QueryEvaluate[` `#` `,` `object` `]`: ([[LavishScript:Object Queries|Object Queries]]) Determines if the given object matches the given query
- ??? `Is64Bit[`???`]`
- ??? `MetaScript[`???`]`
- ??? `MetaScripts[`???`]`
- ??? `LoadMetaScript[`???`]`
- ??? `LoadMetaScriptJSON[`???`]`

### Methods
- `ExecuteAtom[` `name` `,` ... [string](#Type:%20string) `]`: Executes an atom with the given name in global- or script-scope (if a script is currently in context).  Extra parameters are passed as parameters to the atom.
- `RegisterEvent[` `name` `]`: Registers an event of &lt;name>
- `RegisterAlias[`???`]`
- `LoadModule[`???`]`
- `Eval[` `command` `,` [weakref](#Type:%20weakref) `index:string` `]`: Evaluates the given command, directing any lines of output into an index:string
- `RegisterEnum[` `typeName` `,` `bool` `]`: Registers a new enum and LavishScript Object Type with &lt;typeName>. An optional second parameter controls whether the enum is flags, meaning that multiple values may be combined as part of the same value -- if not provided, the default is FALSE. After registering, value names can be added to the enum type via the Enum TLO
- `LoadMetaScript[`???`]`
- `LoadMetaScriptJSON[`???`]`



## Type: script

### Members
- ??? `ID[`???`]`
- [string](#Type:%20string) `Filename`: Filename of this script
- [variable](#Type:%20variable) `Variable[` `name` `]`: A given script-scope variable
- [int](#Type:%20int) `RunningTime`: Number of milliseconds since this script began
- [filepath](#Type:%20filepath) `CurrentDirectory`: Current working directory for this script
- [bool](#Type:%20bool) `Paused`: Scripts current paused state
- [bool](#Type:%20bool) `Profiling`: Profiling status true/false. Debugging must be allowed for profiling to be on.
- [bool](#Type:%20bool) `AllowDebug`: If debugging is allowed
- [string](#Type:%20string) `ExecuteAtom[` `name` `,` ... [string](#Type:%20string) `]`: Executes an atom in script-scope with the given name.  Any extra parameters are passed as parameters to the atom.  If the atom returns a value, the value is given.
- [variablescope](#Type:%20variablescope) `VariableScope`: The scripts variable scope
- ??? `Turbo[`???`]`
- [metascript](#Type:%20metascript) `MetaScript`
- ??? `Retain[`???`]`
- ??? `Function[`???`]`

### Methods
- `End`: Ends execution of this script
- `Squelch`: Squelches most output from this script (excluding most errors and generally excluding Echo)
- `Unsquelch`: Unsquelches
- `QueueCommand[` `command` `]`: Inserts a command in the scripts command queue
- `Pause`: Pauses this script
- `Resume`: Resumes this script
- `ExecuteAtom[` `name` `,` ... [string](#Type:%20string) `]`: Executes an atom in script-scope with the given name.  Any extra parameters are passed as parameters to the atom.
- `EnableProfiling`: Enables script profiling. Debugging must be turned on to enable.
- `DisableProfiling`: Disables script profiling.
- `DisableDebugging`: Disables debugging.
- `DumpStack`: Dumps the current stack into the console.
- `DumpProfiling`: Dumps the entire script into the console.
- `EnableDebugLogging[` `filename` `]`: Enables full debug logging to file.
- `DisableDebugLogging`: Disables full debug logging
- `SetRetain[`???`]`
- `Turbo[`???`]`



## Type: function

### Members
- ??? `Name[`???`]`
- ??? `Metadata[`???`]`

### Methods
none.


## Type: metascript

### Members
- ??? `ID[`???`]`
- ??? `Script[`???`]`

### Methods
- `Start[`???`]`
- `Stop[`???`]`
- `Unload[`???`]`



## Type: variable

### Members
none.
### Methods
none.


## Type: exists
Used to determine validity of an object or Data Sequence

As Text: "TRUE"

### Members
none.
### Methods
none.


## Type: filepath
- Base Type: [unistring](#Type:%20unistring)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- [bool](#Type:%20bool) `PathExists`: TRUE if the given path exists
- [bool](#Type:%20bool) `FileExists[` [additional](#Type:%20additional) `path` `]`: TRUE if the given additional path exists.  This can be a directory OR file, and can be an absolute path or a path relative to this filepath
- [string](#Type:%20string) `Path`: The string representation of this path
- [string](#Type:%20string) `AbsolutePath`: The string representation of this path converted to an absolute path

### Methods
none.


## Type: mutablefilepath
- Base Type: [mutablestring](#Type:%20mutablestring)
- Persistent: No ([weakref](#Type:%20weakref) not supported)



### Members
- ??? `PathExists[`???`]`
- ??? `FileExists[`???`]`
- ??? `Path[`???`]`
- ??? `AbsolutePath[`???`]`

### Methods
- `Set[`???`]`
- `MakeAbsolute[`???`]`
- `MakeSubdirectory[`???`]`



## Type: file
- Persistent: No ([weakref](#Type:%20weakref) not supported)



### Members
- [bool](#Type:%20bool) `Open`: TRUE if the file is open
- [filepath](#Type:%20filepath) `Path`: Full path to this file
- [string](#Type:%20string) `Filename`: Filename of this file
- [string](#Type:%20string) `Read`: Reads a line from this file, up to 1024 characters long (result includes carriage return)
- [string](#Type:%20string) `Read[` `#` `]`: Reads a line from this file, up to # characters long (result includes carriage return)
- [int](#Type:%20int) `ReadBinary[` [binary](#Type:%20binary) `variable` `,` `#` `]`: Reads # bytes into the specified buffer. Result is the number of bytes read.
- [int](#Type:%20int) `Position`: Current position within the file
- [int](#Type:%20int) `Size`: Size of the file
- [bool](#Type:%20bool) `EOF`: TRUE if the previous Read or ReadBinary hit the end of the file

### Methods
- `SetFilename[` `filename` `]`: Sets the full path and filename. Only valid while file is closed.
- `Open`: Opens the file in read-write mode. Creates the file if it does not exist.
- `Open[` `readonly` `]`: Opens the file in read-only mode. Does not create the file if it does not exist.
- `Close`: Closes the file
- `Write[` `text` `]`: Writes the given text to the file
- `WriteBinary[` [binary](#Type:%20binary) `variable` `,` `#` `]`: Writes # bytes from the given buffer variable to the file
- `Seek[` `#` `]`: Seeks to the specified position within the file
- `SeekEnd`: Seeks to the end of the file
- `Skip[` `#` `]`: Skips # bytes within the file
- `Truncate`: Truncates the file at the current position (all data after this point in the file is removed)
- `Flush`: Forces any pending writes to disk.  Writes may otherwise be buffered until the file is closed, or if the file is open for both reading and writing, until a read operation
- `Copy[`???`]`
- `Delete[`???`]`
- `Rename[`???`]`



## Type: filelist
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- [int](#Type:%20int) `Files`: Total file count
- [filelistentry](#Type:%20filelistentry) `File[` `#` `]`: The filelistentry of file &lt;#>

### Methods
- `GetFiles[` `*` `]`: Gets all files from the given directory. (Defaults to current directory and * for files.)
- `GetDirectories[` `*` `]`: Gets all directories from the given directory. (Defaults to current directory)
- `Reset`: Clears the filelist.



## Type: filelistentry
- Persistent: No ([weakref](#Type:%20weakref) not supported)


### Members
- [string](#Type:%20string) `Filename`: Name of the file
- [string](#Type:%20string) `FullPath`: Path+Filename of the file
- [int64ptr](#Type:%20int64ptr) `CreationTime`: Win32 FILETIME (number of 100-nanosecond intervals since January 1, 1601) value representing the time of creation of this file
- [int64ptr](#Type:%20int64ptr) `LastWriteTime`: Win32 FILETIME (number of 100-nanosecond intervals since January 1, 1601) value representing the last time of modification of this file
- [int64ptr](#Type:%20int64ptr) `LastAccessTime`: Win32 FILETIME (number of 100-nanosecond intervals since January 1, 1601) value representing the last time of acces of this file
- [int](#Type:%20int) `Size`: Size in bytes of the file

### Methods
none.


## Type: binary
- Persistent: No ([weakref](#Type:%20weakref) not supported)



### Members
- [intptr](#Type:%20intptr) `Int[` `#` `]`: An int at byte position # of this buffer
- [byteptr](#Type:%20byteptr) `Byte[` `#` `]`: A byte at position # of this buffer
- [floatptr](#Type:%20floatptr) `Float[` `#` `]`: A float at byte position # of this buffer
- [int64ptr](#Type:%20int64ptr) `Int64[` `#` `]`: An int64 at byte position # of this buffer
- [string](#Type:%20string) `String[` `#` `]`: A string at byte position # of this buffer.  NULL if the string is not null-terminated within the size of the buffer
- [uintptr](#Type:%20uintptr) `Uint[` `#` `]`: A uint at byte position # of this buffer
- [boolptr](#Type:%20boolptr) `Bool[` `#` `]`: A bool at byte position # of this buffer
- [uint](#Type:%20uint) `Size`: Size of the buffer

### Methods
- `Resize[` `#` `]`: Resizes the buffer to this many bytes.  Minimum 1, maximum 4194304 (4MB) -- if you need larger for some reason, please let us know.  This is a sanity check
- `Copy[` `buffer` `,` `#` `]`: Copies # bytes from another buffer to position 1 of this buffer
- `Initialize[`???`]`



## Type: scriptobject

### Members
none.
### Methods
none.


## Type: event

### Members
- [int](#Type:%20int) `ID`: ID number of the event (used by modules)
- [string](#Type:%20string) `Name`: Name of the event

### Methods
- `Clear`: Forcefully detach all atoms and C functions from this event
- `AttachAtom[` `name` `]`: Attach an atom to this event
- `DetachAtom[` `name` `]`: Detach an atom from this event
- `Unregister`: Unregister this event
- `Execute[` ... [string](#Type:%20string) `]`: Execute this event, optionally with any number of parameters
- `ThisExecute[` `object` `,` ... [string](#Type:%20string) `]`: Execute this event in the context of a given object, optionally with any number of parameters



## Type: eventvar
- Base Type: [event](#Type:%20event)
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
none.
### Methods
none.


## Type: query

### Members
- ??? `Expression[`???`]`
- ??? `Test[`???`]`

### Methods
none.


## Type: scriptobjecttype

As Text: Same as `Name`

### Members
- ??? `Name[`???`]`
- ??? `Metadata[`???`]`

### Methods
none.


## Type: scriptobjectref

### Members
none.
### Methods
none.


## Type: weakref
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Reference[`???`]`

### Methods
- `SetReference[`???`]`



## Type: objectcontainer

### Members
- [uint](#Type:%20uint) `Size`: Number of objects the container may possibly contain in its present state
- [uint](#Type:%20uint) `Used`: Number of objects presently contained

### Methods
- `Clear`: Clears all objects from the container
- `GetIterator[` [iterator](#Type:%20iterator) `object` `]`: Initializes the given [[ObjectType:iterator|iterator]] object for iteration of this container



## Type: index
- Base Type: [objectcontainer](#Type:%20objectcontainer)

### Members
- [uint](#Type:%20uint) `Next[` `#` `]`: Retrieves the ID of the next valid element in the index, given an ID number
- [sub-type](#Type:%20sub-type) `Get[` `#` `]`: Retrieves the #th element in the index
- [uint](#Type:%20uint) `Insert[` ... [string](#Type:%20string) `]`: Inserts an element in the index.  The parameters will be passed to the object initialization routine for the index sub-type, and an object will be created.  The returned value is the ID of the new element.  The index will be resized to fit the new object if necessary.
- [mutablestring](#Type:%20mutablestring) `Expand[` [begin](#Type:%20begin) `#` `,` `length` `]`: Retrieves the text representation of each existing object in the index as quoted parameters, separated by spaces.  If no parameters are given to Expand, the entire index will be used.  If only the begin # is used, the rest of the index, beginning with the element # specified, will be used.  If the length is additionally given, that number of elements from the index will be used, beginning with the element # specified as the beginning.
- [mutablestring](#Type:%20mutablestring) `ExpandComma[` [begin](#Type:%20begin) `#` `,` `length` `]`: Retrieves the text representation of each existing object in the index as quoted parameters, separated by commas.  If no parameters are given to Expand, the entire index will be used.  If only the begin # is used, the rest of the index, beginning with the element # specified, will be used.  If the length is additionally given, that number of elements from the index will be used, beginning with the element # specified as the beginning.
- [unistring](#Type:%20unistring) `AsJSON`: Returns a JSON array representation of this index, with each element converted by using its AsJSON member

### Methods
- `Shift[` [#](#Type:%20#) `position` `,` [#](#Type:%20#) `places` `]`: Makes room for # places elements at # position, by shifting toward index.Size. The index will not be implicitly Resized, and elements at the end of the index may be destroyed.
- `Sort[`???`]`
- `Remove[` `#` `]`: Removes a single element from the index, by ID
- `RemoveByQuery[` [uint](#Type:%20uint) `query_id` `]`: Erases any elements in the index matching the given [[LavishScript:Object_Queries|Query]]
- `RemoveByQuery[` [uint](#Type:%20uint) `query_id` `,` [bool](#Type:%20bool) `remove_MATCHES` `]`: Erases any elements in the index that either match or do not match the given [[LavishScript:Object_Queries|Query]]
- `Collapse`: Removes gaps in the index (from removal of elements) by shifting elements toward 1
- `Move[` `#` `,` `#` `]`: Moves an element to a new position in the index, by ID numbers.  If an element exists in the new position, it is destroyed
- `Swap[` `#` `,` `#` `]`: Swaps two positions in the index
- `Set[` `#` `,` ... [string](#Type:%20string) `]`: Creates a new element in the index at the given position (destroying the previous element, if it existed).  The additional parameters will be passed to the object initialization routine for the index sub-type, and an object will be created.
- `Insert[` ... [string](#Type:%20string) `]`: Inserts an element in the index.  The parameters will be passed to the object initialization routine for the index sub-type, and an object will be created.  The index will be resized to fit the new object if necessary.
- `Resize[` `#` `]`: Resizes the index such that it will hold at least this number of elements.
- `FromJSON[`???`]`
- `ForEach[` [string](#Type:%20string) `command` `]`: For each element in the index, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration



## Type: collection
- Base Type: [objectcontainer](#Type:%20objectcontainer)

### Members
- [sub-type](#Type:%20sub-type) `Element[` `key` `]`: Retrieves the element, if any, identified by the given key
- ??? `Get[`???`]`
- [sub-type](#Type:%20sub-type) `FirstValue`: Begins iterating with an internal iterator, and retrieves the first value
- [sub-type](#Type:%20sub-type) `NextValue`: Continues iterating with an internal iterator, retrieving the next value
- [string](#Type:%20string) `FirstKey`: Begins iterating with an internal iterator, and retrieves the first key
- [string](#Type:%20string) `NextKey`: Continues iterating with an internal iterator, retrieving the next key
- [string](#Type:%20string) `CurrentKey`: Retrieves the current key in the iteration (with an internal iterator)
- [sub-type](#Type:%20sub-type) `CurrentValue`: Retrieves the current value in the iteration (with an internal iterator)
- [unistring](#Type:%20unistring) `AsJSON`: Returns a JSON object representation of this collection, with each element converted by using its AsJSON member. The keys from the collection will be used as keys in the JSON object
- [unistring](#Type:%20unistring) `AsJSON[` `array` `]`: Returns a JSON array representation of this collection, with each element converted by using its AsJSON member.

### Methods
- `Set[` `key` `,` `value` `]`: Sets (adding, if necessary) the element identified by the given key with the given value
- `FromJSON[`???`]`
- `Erase[` `key` `]`: Erases the element, if any, identified by the given key
- `EraseByQuery[` [uint](#Type:%20uint) `query_id` `]`: Erases any elements in the collection matching the given [[LavishScript:Object_Queries|Query]]
- `EraseByQuery[` [uint](#Type:%20uint) `query_id` `,` [bool](#Type:%20bool) `remove_MATCHES` `]`: Erases any elements in the collection that either match or do not match the given [[LavishScript:Object_Queries|Query]]
- `ForEach[` [string](#Type:%20string) `command` `]`: For each element in the collection, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration



## Type: stack
- Base Type: [objectcontainer](#Type:%20objectcontainer)

### Members
- [sub-type](#Type:%20sub-type) `Top`: Retrieves the first object in the stack

### Methods
- `Push[` ... [string](#Type:%20string) `]`: Adds an object to the stack, passing any parameters to the initialization for the given object type
- `Pop`: Removes the first object in the stack



## Type: queue
- Base Type: [objectcontainer](#Type:%20objectcontainer)

### Members
- [sub-type](#Type:%20sub-type) `Peek`: Retrieves the first object in the queue (first in line)

### Methods
- `Queue[` ... [string](#Type:%20string) `]`: Adds an object to the queue, passing any parameters to the initialization for the given object type
- `Dequeue`: Removes the first object in the queue



## Type: set
- Base Type: [objectcontainer](#Type:%20objectcontainer)

### Members
- [bool](#Type:%20bool) `Contains[` `key` `]`: TRUE if the given key exists in the set
- ??? `FirstKey[`???`]`
- ??? `NextKey[`???`]`
- ??? `CurrentKey[`???`]`
- [unistring](#Type:%20unistring) `AsJSON`: Returns a JSON array representation of this array, with each element converted by using its AsJSON member

### Methods
- `Add[` `key` `]`: Adds a given key to the set
- `Remove[` `key` `]`: Removes a given key from the set
- `Merge[`???`]`
- `Intersect[` [set](#Type:%20set) `A` `,` [set](#Type:%20set) `B` `]`: Adds "sets A and intersect B" to this set
- `Union[` [set](#Type:%20set) `A` `,` [set](#Type:%20set) `B` `]`: Adds "set A union B" to this set
- `Not[` [set](#Type:%20set) `A` `,` [set](#Type:%20set) `B` `]`: Adds "set A not B" to this set
- `ForEach[` [string](#Type:%20string) `command` `]`: For each element in the set, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Value for each iteration



## Type: keyvaluepair
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Key[`???`]`
- ??? `Value[`???`]`

### Methods
none.


## Type: iterator
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- [object](#Type:%20object) `Target`: The iteration target object (such as a set or collection being iterated).  The object type will be the original object type of the object
- [?](#Type:%20?) `Key`: The current key in the iteration.  The object type depends on the data being iterated.
- [object](#Type:%20object) `Value`: The current value in the iteration.  The object type depends on the data being iterated.
- [bool](#Type:%20bool) `IsValid`: Determines if the iterator is valid, pointing to a valid iteration target and key/value
- [bool](#Type:%20bool) `Reversible`: TRUE if the list being iterated also goes backwards, thus making the Previous method valid
- [bool](#Type:%20bool) `Constant`: TRUE if the list will not allow you to set object values (i.e. the values are constant)
- [bool](#Type:%20bool) `RandomAccess`: TRUE if the list allows random access (the iterator:Jump method)

### Methods
- `First`: Sets the iterator position to the first element
- `Last`: Sets the iterator position to the last element
- `Next`: Sets the iterator position to the next element (continues iteration forward)
- `Previous`: Sets the iterator position to the previous element (continues iteration backward)
- `JumpTo[` [string](#Type:%20string) `key` `]`
- `SetValue[` [string](#Type:%20string) `newValue` `]`: Sets the value at the current iterator position



## Type: variablescope

### Members
none.
### Methods
- `CreateVariable[` [object](#Type:%20object) `type` `,` `name` `,` ... [string](#Type:%20string) `]`: Creates a new variable in this scope of the given object type and name.  Any extra parameters are passed to object initialization
- `DeleteVariable[` `name` `]`: Deletes the variable in this scope with the given name, if any
- `Clear`: Deletes all variables within this scope
- `GetIterator[` [iterator](#Type:%20iterator) `object` `]`: Initializes the given [[ObjectType:iterator|iterator]] object for iteration of this variable scope



## Type: enumtype
- Persistent: No ([weakref](#Type:%20weakref) not supported)


### Members
- [string](#Type:%20string) `Name`: Name of the enum type
- [int64](#Type:%20int64) `ValueByName[` `name` `]`: Retrieves a value by its name
- [string](#Type:%20string) `NameByValue[` `#` `]`: Retrieves a name by a given value (or for flags, a set of names from the combined value)

### Methods
- `SetValue[` `name` `,` `#` `]`: Assigns a value to a given name
- `GetIterator[` `iterator` `]`: Sets an iterator for iterating the available values



## Type: jsonvalue

As Text: JSON representation of the value

### Members
- [string](#Type:%20string) `AsString`: The contained value as a string
- [unistring](#Type:%20unistring) `AsJSON[` <"multiline"> `]`: The contained value as multiline JSON text. multiline is literal, e.g. ${MyValue.AsJSON[multiline]}
- [string](#Type:%20string) `AsJSON`: The contained value as single-line JSON text
- [string](#Type:%20string) `Type`: The type of JSON object stored; one of: null, object, string, number, array, true, false, integer. Note that while the JSON standard does not differentiate between floating-point numbers and integers, LavishScript does
- [object](#Type:%20object) `Value`: The contained value

### Methods
- `WriteFile[` [string](#Type:%20string) `filePath` `,` <"multiline"> `,` <[string](#Type:%20string) `lineSplit`="\\r\\n"> `]`: Writes the JSON to file, optionally in multi-line form, with a specified line splitter
- `WriteFile[` `filename` `]`: Writes the JSON to file, in condensed single-line form.
- `WriteFile[` `filename` `,` `multiline` `]`: Writes the JSON to file, optionally in multi-line form, with "\r\n" (Windows) line splitting



## Type: jsoniterator
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- [jsonvalue](#Type:%20jsonvalue) `Target`
- ??? `Key`
- [jsonvalue](#Type:%20jsonvalue) `Value`
- [bool](#Type:%20bool) `IsValid`
- [bool](#Type:%20bool) `Reversible`
- [bool](#Type:%20bool) `Constant`
- [bool](#Type:%20bool) `RandomAccess`

### Methods
- `First`
- `Last`
- `Next`
- `Previous`
- `JumpTo[` [string](#Type:%20string) `key` `]`
- `SetValue[` [jsonvalue](#Type:%20jsonvalue) `newValue` `]`



## Type: jsonvaluecontainer
- Base Type: [jsonvalue](#Type:%20jsonvalue)

### Initializers
- `jsonvaluecontainer[` [jsonvalue](#Type:%20jsonvalue) `newValue` `]`

As Text: JSON representation of the value

### Members
- [string](#Type:%20string) `AsString`: The contained value as a string
- [unistring](#Type:%20unistring) `AsJSON[` <"multiline"> `]`: The contained value as multiline JSON text
- [string](#Type:%20string) `AsJSON`: The contained value as single-line JSON text
- [string](#Type:%20string) `Type`: The type of JSON object stored; one of: null, object, string, number, array, true, false, integer. Note that while the JSON standard does not differentiate between floating-point numbers and integers, LavishScript does
- [jsonvaluecontainer](#Type:%20jsonvaluecontainer) `Value`: The contained value

### Methods
- `SetValue[` <"-lazy"> `,` [jsonvalue](#Type:%20jsonvalue) `newValue` `]`
- `SetValue[` `json` `]`: Sets the contained json value, e.g. myJsonValueContainer:SetValue["{\"someValue\":17}"] will set myJsonValueContainers value to a jsonobject that in turn contains one value
- `ParseFile[` [string](#Type:%20string) `filename` `]`: Sets the contained json value to the contents of a specified json file



## Type: jsonvalueref

### Initializers
- `jsonvalueref[` [weakref](#Type:%20weakref) `jsonValue` `]`

As Text: JSON representation of the referenced value

### Members
- [jsonvalue](#Type:%20jsonvalue) `Reference`

### Methods
- `SetReference[` [weakref](#Type:%20weakref) `jsonValue` `]`



## Type: jsonarray

### Indexers
- [object](#Type:%20object) `jsonarray[` ... [string](#Type:%20string) `fieldPath` `]`

As Text: JSON representation of the array

### Members
- [object](#Type:%20object) `Get[` ... [string](#Type:%20string) `fieldPath` `]`: Gets a value stored within this array, by its index (1-based)
- [...](#Type:%20...) `Get[` `#` `,` `valueName2` `,` ... [string](#Type:%20string) `]`: Gets a stored value multiple levels deep within jsonarrays and/or jsonobjects
- [uint](#Type:%20uint) `Size`: Allocated capacity of the array
- [uint](#Type:%20uint) `Used`: Total number of values currently in the array
- [string](#Type:%20string) `Type`
- [string](#Type:%20string) `AsString`
- [unistring](#Type:%20unistring) `AsJSON[` <"multiline"> `]`
- [jsonarray](#Type:%20jsonarray) `Value`

### Methods
- `GetIterator[` [weakref](#Type:%20weakref) `iteratorObject` `]`: Sets a jsoniterator to iterate this JSON array
- `Clear`: Clears all values from the array
- `Set[` <"-lazy"> `,` ... [string](#Type:%20string) `fieldPath` `,` [jsonvalue](#Type:%20jsonvalue) `newValue` `]`
- `Set[` `#` `,` `json` `]`: Sets a value within the array, to a new JSON value of any type, e.g. &lt;tt>myJsonArray:Set[1,"{\"subValue\":12}"]&lt;/tt>
- `Add[` [jsonvalue](#Type:%20jsonvalue) `newValue` `]`: Adds a value to the end of the array, to a new JSON value of any type, e.g. &lt;tt>myJsonArray:Add["{\"subValue\":12}"]&lt;/tt>
- `Sort[` <[string](#Type:%20string) `keyProperty`> `]`
- `Erase[` [uint](#Type:%20uint) `key` `]`: Erases the nth value from the array, shifting later items toward 0
- `EraseByQuery[` [string](#Type:%20string) `queryText` `,` <[bool](#Type:%20bool) `removeMatches`=true> `]`: Erases items either matching or not matching the query from the array (depending on the 2nd parameter), shifting later elements toward 0
- `EraseByQuery[` [Query](#Type:%20Query) `ID` `]`: Erases items matching the query from the array, shifting later elements toward 0
- `WriteFile[` [string](#Type:%20string) `filePath` `,` <"multiline"> `,` <[string](#Type:%20string) `lineSplit`="\\r\\n"> `]`
- `ForEach[` [string](#Type:%20string) `command` `]`: For each element in the array, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration



## Type: jsonobject

### Indexers
- [object](#Type:%20object) `jsonobject[` ... [string](#Type:%20string) `fieldPath` `]`

As Text: JSON representation of the object

### Members
- [object](#Type:%20object) `Get[` ... [string](#Type:%20string) `fieldPath` `]`: Gets a value stored within this object, by its name
- [...](#Type:%20...) `Get[` `valueName` `,` `valueName2` `,` ... [string](#Type:%20string) `]`: Gets a stored value multiple levels deep within jsonobjects and/or jsonarrays
- [string](#Type:%20string) `Type`
- [string](#Type:%20string) `AsString`
- [unistring](#Type:%20unistring) `AsJSON[` <"multiline"> `]`
- [jsonobject](#Type:%20jsonobject) `Value`
- [bool](#Type:%20bool) `Has[` ... [string](#Type:%20string) `fieldPath` `]`: Checks whether a value is stored within this object, by its name
- [bool](#Type:%20bool) `Has[` `valueName` `,` `valueName2` `,` ... [string](#Type:%20string) `]`: Checks whether a value is stored, multiple levels deep within jsonobjects and/or jsonarrays
- [bool](#Type:%20bool) `Assert[` <"-lazy"> `,` ... [string](#Type:%20string) `fieldPath` `,` [jsonvalue](#Type:%20jsonvalue) `matchValue` `]`
- [bool](#Type:%20bool) `Assert[` `valueName` `,` `json` `]`: Checks whether a value is stored within this object AND matches the specified JSON value
- [bool](#Type:%20bool) `Assert[` `valueName` `,` `valueName2` `,` ... [string](#Type:%20string) `,` `json` `]`: Checks whether a value is stored, multiple levels deep within jsonobjects and/or jsonarrays, AND matches the specified JSON value
- [jsonarray](#Type:%20jsonarray) `Keys`: A JSON array containing a list of keys from this object
- [jsonarray](#Type:%20jsonarray) `Values`: A JSON array containing a list of values from this object

### Methods
- `GetIterator[` [weakref](#Type:%20weakref) `iteratorObject` `]`: Sets a jsoniterator to iterate this JSON object
- `Clear`: Clears all values from the object
- `Set[` <"-lazy"> `,` ... [string](#Type:%20string) `fieldPath` `,` [jsonvalue](#Type:%20jsonvalue) `newValue` `]`
- `Set[` `valueName` `,` `json` `]`: Sets a value within the object, to a new JSON value of any type, e.g. &lt;tt>myJsonObject:Set["someObject","{\"subValue\":12}"]&lt;/tt>
- `Erase[` [string](#Type:%20string) `fieldName` `]`: Erases the specified value from the object
- `EraseByQuery[` [string](#Type:%20string) `queryText` `,` <[bool](#Type:%20bool) `removeMatches`=true> `]`: Erases items either matching or not matching the query from the object (depending on the 2nd parameter)
- `EraseByQuery[` [Query](#Type:%20Query) `ID` `]`: Erases items matching the query from the object
- `WriteFile[` [string](#Type:%20string) `filePath` `,` <"multiline"> `,` <[string](#Type:%20string) `lineSplit`="\\r\\n"> `]`
- `ForEach[` [string](#Type:%20string) `command` `]`: For each value in the object, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration



## Type: lavishmachine
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- [taskmanager](#Type:%20taskmanager) `NewTaskManager[` `name` `]`: Creates a new, empty, [[LavishScript:Task Manager|Task Manager]], or provides the existing Task Manager by the given name
- [tasktypeset](#Type:%20tasktypeset) `NewTaskTypeSet[` `name` `]`: Creates a new, empty, [[LavishScript:Task Type Set|Task Type Set]]
- [tasktype](#Type:%20tasktype) `NewTaskType[` `json` `]`: Creates a new [[LavishScript:Task Type|Task Type]] from a supplied JSON object
- [tasklibrary](#Type:%20tasklibrary) `NewTaskLibrary[` `name` `]`: Creates a new, empty, [[LavishScript:Task Library|Task Library]], or provides the existing Task Library by the given name
- [taskmanager](#Type:%20taskmanager) `TaskManager[` `#` `]`: Retrieves a Task Manager by ID
- [tasktypeset](#Type:%20tasktypeset) `TaskTypeSet[` `#` `]`: Retrieves a Task Type Set by ID
- [tasktype](#Type:%20tasktype) `TaskType[` `#` `]`: Retrieves a Task Type by ID
- [tasklibrary](#Type:%20tasklibrary) `TaskLibrary[` `#` `]`: Retrieves a Task Library by ID
- [task](#Type:%20task) `Task[` `#` `]`: Retrieves a running Task by ID

### Methods
- `LoadPackageFile[` `filename` `]`: Loads a [[LavishMachine:Package|LavishMachine Package]] from a file containing a JSON object
- `LoadPackageJSON[` `json` `]`: Loads a [[LavishMachine:Package|LavishMachine Package]] from a supplied JSON object
- `LoadTaskTypesFile[` `filename` `]`: Loads [[LavishMachine:Task Types|Task Types]] from a file containing a JSON array
- `LoadTaskTypesJSON[` `json` `]`: Loads [[LavishMachine:Task Types|Task Types]] from a supplied JSON array



## Type: taskpulseargs

### Members
- [task](#Type:%20task) `Task`: The current Task instance to process
- [int64](#Type:%20int64) `Timestamp`: Current Timestamp value, as can be compared to task.StartTimestamp and task.LastFrameTimestamp
- [uint](#Type:%20uint) `ElapsedMS`: Elapsed time, in milliseconds, since the Task started
- [elmactaskstate](#Type:%20elmactaskstate) `TaskState`: One of Start, Continue, or Stop. This indicates the current state of the Task.
- [unistring](#Type:%20unistring) `Error`: The Error, if any, as would be set by taskpulseargs:SetError

### Methods
- `SetError[` `text` `]`: Sets error text associated with the Task



## Type: task

### Members
- [string](#Type:%20string) `Name`: Name of the Task, if one was provided
- [int64](#Type:%20int64) `ID`: ID of the Task
- [tasktype](#Type:%20tasktype) `Type`: Task Type (such as "ls1.echo")
- ??? `TaskManager[`???`]`
- [jsonobject](#Type:%20jsonobject) `Args`: A copy of the object used to initiate the Task, held for the Tasks lifetime. This object can be modified during use to store additional information.
- [jsonvalue](#Type:%20jsonvalue) `Args[` ... [string](#Type:%20string) `]`: Shortcut to retrieve a value from Args, e.g. Task.Args[someObject,someValue] is the same as Task.Args.Get[someObject].Get[someValue] or Task.Args.Get[someObject,someValue]
- [jsonobject](#Type:%20jsonobject) `Result`: The Result object produced by the Task (currently unused)
- [jsonvalue](#Type:%20jsonvalue) `Result[` ... [string](#Type:%20string) `]`: Shortcut to retrieve a value from Result
- [bool](#Type:%20bool) `IsRunning`: TRUE if the Task is currently running.
- [float](#Type:%20float) `RunningTime`: Running Time of the Task, in seconds. NULL if the Task is not running.
- [int64](#Type:%20int64) `RunningTimeMS`: Running Time of the Task, in milliseconds. NULL if the Task is not running.
- [float](#Type:%20float) `FrameElapsed`: Amount of time since the previous Task Frame (Pulse of the Task), in seconds. NULL if the Task is not running.
- [int64](#Type:%20int64) `FrameElapsedMS`: Amount of time since the previous Task Frame (Pulse of the Task), in milliseconds. NULL if the Task is not running.
- [int64](#Type:%20int64) `StartTimestamp`: The timestamp when the Task was started. NULL if the Task is not running.
- [int64](#Type:%20int64) `LastFrameTimestamp`: The timestamp of the previous Task Frame (Pulse of the Task). NULL if the Task is not running.
- [float](#Type:%20float) `Duration`: The defined duration of the Task, in seconds. NULL if the Task does not have a specified duration.
- [int64](#Type:%20int64) `DurationMS`: The defined duration of the Task, in milliseconds. NULL if the Task does not have a specified duration.
- [bool](#Type:%20bool) `IsInstant`: TRUE if the Task is defined as instant

### Methods
- `Start`: Start the Task
- `Stop`: Stop the Task
- `Toggle`: Stop or Start the Task



## Type: tasktype

### Members
- [string](#Type:%20string) `Name`: Name of the Task Type
- [uint](#Type:%20uint) `ID`: The ID number assigned to the Task Type

### Methods
- `Unregister`: Unregisters the Task Type. The Task Type can no longer be used to begin Tasks



## Type: tasktypeset
- Persistent: No ([weakref](#Type:%20weakref) not supported)

### Members
- ??? `Name[`???`]`
- ??? `ID[`???`]`

### Methods
none.


## Type: tasklibrary

### Members
- [string](#Type:%20string) `Name`: Name of the Task Library
- [int64](#Type:%20int64) `ID`: ID of the Task Library
- ??? `AsJSON[`???`]`
- [jsonvalue](#Type:%20jsonvalue) `Task[` `name` `]`: Retrieve the stored JSON object that defines a Task by a given name. Because a Task Library "is" a JSON object, .Task[name] does the same as .JSON[name]

### Methods
- `Clear`: Clears all Tasks defined in the Task Library
- `Destroy`: Destroys the Task Library, such that it can no longer be found via [[ObjectType:lavishmachine|lavishmachine]].TaskLibrary[name]
- `AddTask[` `name` `,` `jsonobject` `]`: Adds a new Task by name. A Task is defined by a JSON object. Example:   MyTaskLibrary:AddTask[Hello World,"{\"type\":\"ls1.echo\",\"output\":\"Hello World!\"}"]
- `RemoveTask[` `name` `]`: Removes a defined Task by name



## Type: taskmanager

### Members
- [string](#Type:%20string) `Name`: Name of the Task Manager
- [uint](#Type:%20uint) `ID`: The ID number assigned to the Task Manager
- [task](#Type:%20task) `BeginTask[` `jsonobject` `]`: Begins a Task via the provided JSON object, e.g. &lt;tt>TaskManager:BeginTask["{\"type\":\"ls1.echo\",\"output\":\"Hello World!\"}"]&lt;/tt>
- [task](#Type:%20task) `BeginTaskLibrary[` `name` `]`: Begins every Task in a given Task Library, wrapped in a parallel Task

### Methods
- `SetTaskTypeSet[`???`]`
- `BeginTask[` `jsonobject` `]`: Begins a Task via the provided JSON object, e.g. &lt;tt>TaskManager:BeginTask["{\"type\":\"ls1.echo\",\"output\":\"Hello World!\"}"]&lt;/tt>
- `BeginTaskLibrary[` `name` `]`: Begins every Task in a given Task Library, wrapped in a parallel Task
- `Clear`: Stops all running Tasks
- `Destroy`: Stops all running Tasks, and destroys the Task Manager itself
- `BeginTasksFile[`???`]`
- `BeginTasks[` `jsonarray` `]`: Begins every Task in a given JSON array of Task objects



LavishGUI 2 API Specification (LavishScript)

---
# Events
none.

---
# Commands
none.

---
# Top-Level Objects
## TLO: LGUI2
- [lgui2](#Type:%20lgui2) `LGUI2`


---
# Types
## Type: lgui2
- Base Type: [lgui2layer](#Type:%20lgui2layer)

As Text: "LavishGUI 2.0"

### Members
- [lgui2layer](#Type:%20lgui2layer) `Layer`
- [lgui2element](#Type:%20lgui2element) `Element[` [uint](#Type:%20uint) `id` `]`: Retrieves an Element by ID #
- [lgui2element](#Type:%20lgui2element) `Element[` ... [string](#Type:%20string) `locateArgs` `]`
- [...](#Type:%20...) `Element[` `elementName` `,` `elementType` `,` `locateFlags` `]`: [[LGUI2:Locate|Locates]] an Element
- [lgui2elementtype](#Type:%20lgui2elementtype) `ElementType[` [string](#Type:%20string) `name` `]`: Retrieves an Element Type by name
- [lgui2animationtype](#Type:%20lgui2animationtype) `AnimationType[` [string](#Type:%20string) `name` `]`: Retrieves an [[LGUI2:Animation Type|Animation Type]] by name
- [lgui2skin](#Type:%20lgui2skin) `Skin[` <[string](#Type:%20string) `name`> `]`: Retrieves a Skin by name
- [lgui2skin](#Type:%20lgui2skin) `Skin`: The currently active Skin
- [jsonvalue](#Type:%20jsonvalue) `Template[` [string](#Type:%20string) `name` `]`: Retrieves a skinned Template, applying the current Skin stack
- [jsonvalue](#Type:%20jsonvalue) `TemplateValue[` [string](#Type:%20string) `templateName` `,` [string](#Type:%20string) `valueName` `]`: Retrieves a skinned Template value, applying the current Skin stack
- [object](#Type:%20object) `DataBindingContext`: When processing a [[LGUI2:Data Binding|Data Binding]], this is the element or other object that owns the binding
- [object](#Type:%20object) `TriggerContext`: When processing a [[LGUI2:Trigger|Trigger]], this is the element or other object that owns the trigger

### Methods
- `Clear`
- `LoadSkinFile[` [string](#Type:%20string) `filename` `]`
- `PushSkin[` [string](#Type:%20string) `skinName` `]`: Pushes a [[LGUI2:Skin|Skin]] by name onto the Skin stack
- `PopSkin[` [string](#Type:%20string) `skinName` `]`: Pops a [[LGUI2:Skin|Skin]] by name off of the Skin stack, if it is the top of the stack
- `UnloadSkinFile[` [string](#Type:%20string) `filename` `]`
- `RegisterAnimationType[` [jsonobject](#Type:%20jsonobject) `jsonValue` `]`
- `LoadTextElementTypesFile[` [string](#Type:%20string) `filename` `]`
- `LoadTextElementTypesJSON[` [jsonobject](#Type:%20jsonobject) `jsonValue` `]`
- `LoadTextElementTypeJSON[` [jsonobject](#Type:%20jsonobject) `jsonValue` `]`
- `DumpProfiling`



## Type: lgui2eventargs

As Text: "lgui2eventargs"

### Members
- [jsonobject](#Type:%20jsonobject) `Source`: The source of the event being fired.
- [jsonobject](#Type:%20jsonobject) `Args`: Any properties passed with the event
- [jsonvalue](#Type:%20jsonvalue) `Args[` [string](#Type:%20string) `key` `]`: A value from the Args object, by its key
- [bool](#Type:%20bool) `Handled`: TRUE if the event has been acknowledged as handled.

### Methods
- `SetHandled`: Sets the event "Handled" state to TRUE. This is generally recommended within event handlers. Hooks in particular will ignore the Handled state.



## Type: lgui2animateargs

As Text: "lgui2animateargs"

### Members
- [lgui2element](#Type:%20lgui2element) `Element`: The [[LGUI2:Element|Element]] to animate
- [lgui2animation](#Type:%20lgui2animation) `Animation`: The Animation object
- [jsonobject](#Type:%20jsonobject) `Args`: The Item data (also accessible via Item.Data)
- [jsonvalue](#Type:%20jsonvalue) `Args[` `key` `]`: Retrieves a value from the Item data
- [uint](#Type:%20uint) `Timestamp`: The current Timestamp
- [elgui2animationframestate](#Type:%20elgui2animationframestate) `FrameState`: The current state (Start, Continue, Stop)
- [unistring](#Type:%20unistring) `Error`: An error message set by the SetError method, indicating an error condition on the Animation (and resulting in a Stop)

### Methods
- `SetError[` `error` `]`: An error message to indicate an error condition on a custom Animation. The Animation will Stop.



## Type: lgui2itemviewgeneratorargs


### Members
- [lgui2item](#Type:%20lgui2item) `Item`: The Item to generate a view for
- [unistring](#Type:%20unistring) `ItemType`: The type of Item, either "default" or an explicitly specified value also present in Args
- [jsonobject](#Type:%20jsonobject) `Args`: The Item data (also accessible via Item.Data)
- [jsonvalue](#Type:%20jsonvalue) `Args[` ... [string](#Type:%20string) `fieldPath` `]`: Retrieves a value from the Item data
- [lgui2element](#Type:%20lgui2element) `Parent`: The parent [[LGUI2:Element|Element]] which will contain the Item View (e.g. the ItemsContainer of an [[LGUI2:Item List|Item List]])
- [lgui2element](#Type:%20lgui2element) `View`: The [[LGUI2:Element|Element]] to represent the Item, if it has been set by the Item View Generator
- [unistring](#Type:%20unistring) `Error`: The Error text, if it has been set by the Item View Generator

### Methods
- `SetView[` [jsonobject](#Type:%20jsonobject) `jsonValue` `]`: Creates a new [[LGUI2:Element|Element]] (View) to represent the Item
- `SetError[` [string](#Type:%20string) `errorText` `]`: Sets a new Error value



## Type: lgui2canvasrenderer


### Members
- [lgui2fontstyle](#Type:%20lgui2fontstyle) `Font[` [string](#Type:%20string) `name` `]`
- [lgui2brush](#Type:%20lgui2brush) `Brush[` [string](#Type:%20string) `name` `]`
- [float](#Type:%20float) `CanvasHeight`
- [float](#Type:%20float) `CanvasWidth`

### Methods
- `ClearCanvas[`???`]`
- `InitializeCanvas[`???`]`
- `SetCanvasSize[`???`]`
- `Reset`
- `SetFont[`???`]`
- `SetBrush[`???`]`
- `PushFont[`???`]`
- `PushBrush[`???`]`
- `PopBrush[`???`]`
- `PopFont[`???`]`
- `DrawRect[`???`]`
- `DrawText[`???`]`
- `DrawCircle[`???`]`
- `DrawArc[`???`]`
- `DrawPrimitives[`???`]`
- `PushTransform[`???`]`
- `SetTransform[`???`]`
- `PopTransform[`???`]`
- `PushBlendMode[`???`]`
- `PopBlendMode[`???`]`
- `Batch[`???`]`



## Type: lgui2brush

As Text: "lgui2brush"

### Members
- [int](#Type:%20int) `Color`: The Color value applied to the brush
- [elgui2imageorientation](#Type:%20elgui2imageorientation) `ImageOrientation`: Transforms to apply to the image
- [string](#Type:%20string) `ImageFilename`: The filename of an image to use for this Brush, if any
- [int](#Type:%20int) `ImageTransparencyKey`: The transparency key value used for the image
- ??? `ImageBrushName[`???`]`
- [jsonvalue](#Type:%20jsonvalue) `PixelShader`: Pixel Shader initialization data, if any
- ??? `VertexShader[`???`]`
- ??? `AsJSON[`???`]`
- ??? `Canvas[`???`]`

### Methods
- `SetColor[` `#aarrggbb` `]`: Sets the new Color value for the brush. e.g. :SetColor["#ffffff"] -- also accepts #rrggbb
- `SetImageOrientation[` [elgui2imageorientation](#Type:%20elgui2imageorientation) `]`
- `SetImage[` `filename` `]`
- `SetImage[` `filename` `,` `colorKey` `]`
- `SetImageBrushName[`???`]`
- `SetPixelShader[` `json` `]`
- `SetVertexShader[`???`]`
- `SetCanvas[`???`]`



## Type: lgui2animation

As Text: "lgui2animation"

### Members
- [unistring](#Type:%20unistring) `Name`: The name of the Animation
- [lgui2element](#Type:%20lgui2element) `Element`: The Element being animated
- [lgui2animationtype](#Type:%20lgui2animationtype) `Type`: The Animation Type doing the animating
- [jsonobject](#Type:%20jsonobject) `Parameters`: Parameters used to create the Animation. Any changes/additions to this object are kept for the lifetime of the Animation.
- [bool](#Type:%20bool) `IsRunning`: TRUE if the Animation is running
- [float](#Type:%20float) `RunningTime`: Running time (elapsed time) of the Animation, in seconds
- [uint](#Type:%20uint) `RunningTimeMS`: Running time (elapsed time) of the Animation, in milliseconds
- ??? `FrameElapsed[`???`]`
- ??? `FrameElapsedMS[`???`]`
- [uint](#Type:%20uint) `StartTimestamp`: The Animations Start time (milliseconds)
- [uint](#Type:%20uint) `LastFrameTimestamp`: The Animations last frame (milliseconds)
- [float](#Type:%20float) `Duration`: Specified duration (total expected length of time) of the Animation, if any, given in seconds
- [uint](#Type:%20uint) `DurationMS`: Specified duration (total expected length of time) of the Animation, if any, given in milliseconds
- [bool](#Type:%20bool) `IsInstant`: TRUE if the Animation is instant

### Methods
- `Start`: Start the Animation
- `Stop`: Stop the Animation
- `Toggle`: Start/Stop the Animation
- `SetInstant[` `bool` `]`: Sets the Instant flag to the specified value
- `SetDuration[` `float` `]`: Sets the duration of the Animation in seconds, with floating point (e.g. 1.5 for 1.5 seconds)
- `SetDurationMS[` `#` `]`: Sets the duration of the Animation in milliseconds (e.g. 1500 for 1.5 seconds)



## Type: lgui2thickness

As Text: left,top,right,bottom

### Members
- ??? `Left[`???`]`
- ??? `Top[`???`]`
- ??? `Right[`???`]`
- ??? `Bottom[`???`]`

### Methods
none.


## Type: lgui2fontstyle

As Text: "lgui2fontstyle"

### Members
- [string](#Type:%20string) `Face`: Face of the font, such as "Arial"
- [uint](#Type:%20uint) `Height`: Font height, in points
- ??? `HeightFactor[`???`]`
- ??? `HeightOffset[`???`]`
- [bool](#Type:%20bool) `Fixed`: TRUE if the font requests fixed width glyphs
- [bool](#Type:%20bool) `Bold`: TRUE if the font is bold
- [elgui2fontflags](#Type:%20elgui2fontflags) `Flags`: Flags indicating which of the font style properties are explicitly provided, rather than inherited

### Methods
- `SetFace[` `newFace` `]`: Sets a new Face for this font
- `UnsetFace`: Un-sets the Face property from this font, causing this property to be inherited
- `SetHeight[` `#` `]`: Sets a new Height for this font, in points
- `UnsetHeight`: Un-sets the Height property from this font, causing this property to be inherited
- `SetHeightFactor[`???`]`
- `SetHeightOffset[`???`]`
- `SetFixed[` `TRUE/FALSE` `]`: Sets the fixed width request state for this font
- `UnsetFixed`: Un-sets the Fixed property from this font, causing this property to be inherited
- `SetBold[` `TRUE/FALSE` `]`: Sets the Bold state for this font
- `UnsetBold`: Un-sets the Bold property from this font, causing this property to be inherited



## Type: lgui2eventhandler

As Text: "lgui2eventhandler"

### Members
- [lgui2element](#Type:%20lgui2element) `Owner`: The element that owns this Event Handler
- ??? `AsJSON[`???`]`

### Methods
none.


## Type: lgui2databinding

As Text: "lgui2databinding"

### Members
- ??? `BufferSize[`???`]`
- ??? `IsAutoPull[`???`]`
- ??? `IsAutoPush[`???`]`
- ??? `IsAutoPullOnce[`???`]`
- ??? `PullReplaceNULL[`???`]`
- ??? `PullFormat[`???`]`
- ??? `PushFormat[`???`]`
- ??? `PushNULLFormat[`???`]`
- ??? `PullValue[`???`]`
- ??? `AsJSON[`???`]`

### Methods
- `SetBufferSize[`???`]`
- `SetAutoPull[`???`]`
- `SetAutoPullOnce[`???`]`
- `SetAutoPush[`???`]`
- `SetPullReplaceNULL[`???`]`
- `SetPullFormat[`???`]`
- `SetPushFormat[`???`]`
- `SetPushNULLFormat[`???`]`
- `PushValue[`???`]`
- `PullValue[`???`]`
- `ApplyStyleJSON[`???`]`



## Type: lgui2inputbinding

As Text: Same as `Name`

### Members
- ??? `Name[`???`]`
- [lgui2eventhandler](#Type:%20lgui2eventhandler) `EventHandler`: The Event Handler that will fire when this Input Binding is activated

### Methods
- `SetName[` `newName` `]`: Changes the name of this Input Binding
- `Remove[`???`]`



## Type: lgui2trigger

As Text: Same as `Name`

### Members
- ??? `Name[`???`]`
- [lgui2eventhandler](#Type:%20lgui2eventhandler) `EventHandler[` `matched|unmatched` `]`: The Event Handler that will fire when this Trigger is either matched or unmatched (depending on the parameter)

### Methods
- `Update`: Updates the Trigger, automatically checking the condition again
- `Update[` [bool](#Type:%20bool) `matched` `]`: Updates the Trigger, manually specifying whether the condition is now matched (TRUE) or unmatched (FALSE)
- `SetName[` `newName` `]`: Changes the name of this Trigger
- `Remove`: Removes the Trigger



## Type: lgui2inputhook

As Text: Same as `Name`

### Members
- ??? `Name[`???`]`
- ??? `EventHandler[`???`]`

### Methods
- `SetName[`???`]`
- `Remove[`???`]`



## Type: lgui2item

As Text: "lgui2item"

### Members
- [lgui2itemlist](#Type:%20lgui2itemlist) `ItemList`: The element hosting this Item
- [unistring](#Type:%20unistring) `Type`: The Item type
- [jsonvalue](#Type:%20jsonvalue) `Data`: The Item data
- [int64](#Type:%20int64) `Index`: The Items index in the ItemList
- [bool](#Type:%20bool) `Selected`: TRUE if the item is selected
- [lgui2element](#Type:%20lgui2element) `View[` `#` `]`: Retrieve an Item view, by the views parent element ID (usually the ItemList.ItemsContainer.ID)
- ??? `Depth[`???`]`
- ??? `Expanded[`???`]`

### Methods
- `SetSelected[` `bool` `]`: Selects or de-selects the Item
- `SetExpanded[`???`]`
- `ToggleExpanded[`???`]`
- `Remove`: Removes the Item from the Item List
- `ClearChildren[`???`]`



## Type: lgui2radialitem

As Text: "lgui2radialitem"

### Members
- [lgui2radialpanel](#Type:%20lgui2radialpanel) `RadialPanel`: The Radial Panel containing this Radial Item
- [lgui2element](#Type:%20lgui2element) `Element`: The Child of Radial Panel represented by this Radial Item
- [float](#Type:%20float) `ArcLength`: The desired arc length, in degrees, of this Radial Item
- [float](#Type:%20float) `ActualArcLength`: The actual arc length, in degrees, of this Radial Item, after layout
- [float](#Type:%20float) `InnerRadius`: The inner radius (distance from the center of the panel) of this Radial Item
- [float](#Type:%20float) `OuterRadius`: The outer radius (distance from the center of the panel) of this Radial Item. (OuterRadius >= InnerRadius)
- ??? `ZoneMargin[`???`]`
- ??? `LiveZone[`???`]`
- [float](#Type:%20float) `ActualArcLocation`: The actual arc location of this Radial Item, after layout
- [bool](#Type:%20bool) `Contains[` `degreesClockwise` `,` `distance` `]`: TRUE if this Radial Item contains the point at the given vector from the center of the RadialPanel
- [bool](#Type:%20bool) `ContainsPoint[` `#` `,` `#` `]`: TRUE if this Radial Item contains the given X,Y coordinate (relative to the Layer, i.e. the game window)
- [bool](#Type:%20bool) `IsMouseOver`: TRUE if the mouse cursor is over the Radial Item (i.e. ContainsPoint[${Mouse}])
- [float](#Type:%20float) `Opacity`: Opacity value for the Radial Item (usually between 0.0 and 1.0, with 1.0 being 100% opaque and 0.0 being fully transparent)
- [lgui2margins](#Type:%20lgui2margins) `BorderThickness`: Retrieves the thickness of the border
- [lgui2brush](#Type:%20lgui2brush) `BorderBrush`: Retrieves the Brush for the border itself, if applicable
- [lgui2brush](#Type:%20lgui2brush) `BackgroundBrush`: Retrieves the Brush for the background of the area surrounded by the border, if applicable
- [jsonvalue](#Type:%20jsonvalue) `Style[` `name` `]`: Retrieves a [[LGUI2:Style|Style]] by name

### Methods
- `SetArcLength[` `#` `]`: Sets the desired arc length, in degrees, of this Radial Item
- `SetZoneMargin[`???`]`
- `SetLiveZone[`???`]`
- `SetArcMargins[` `#` `]`: Sets the left and right arc margins (in degrees) to this value
- `SetOpacity[` `#` `]`: Sets the Opacity value for the Radial Item, with 0.0 being transparent and 1.0 being opaque
- `SetBorderThickness[` `#` `]`: Sets all of this elements BorderThickness values to this #
- `SetBorderThickness[` `#` `,` `#` `]`: Sets Left/Right and Top/Bottom (Inner/Outer) BorderThickness values to these #s (in that order)
- `SetBorderThickness[` `#` `,` `#` `,` `#` `,` `#` `]`: Sets Left, Top (Outer), Right, Bottom (Inner) BorderThickness values to these #s (in that order)
- `SetBorderBrush[` `json` `]`: Sets the [[LGUI2:Brush|Brush]] used for the border around the Radial Item
- `SetBackgroundBrush[` `json` `]`: Sets the [[LGUI2:Brush|Brush]] used for the background of the area surrounded by the border, if applicable
- `ApplyStyle[` `name` `]`: Applies a [[LGUI2:Style|Style]] by name
- `ApplyStyleJSON[` `json` `]`: Applies a [[LGUI2:Style|Style]] defined by the provided json
- `SetStyle[` `name` `,` `json` `]`: Adds a [[LGUI2:Style|Style]] with the provided name to the element
- `RemoveStyle[` `name` `]`: Removes a [[LGUI2:Style|Style]] by name



## Type: lgui2radialgaugeneedle

As Text: "lgui2radialgaugeneedle"

### Members
- [lgui2radialgauge](#Type:%20lgui2radialgauge) `RadialGauge`: The Radial Gauge containing this Radial Gauge Needle
- [unistring](#Type:%20unistring) `Name`: The Name of the needle
- [jsonobject](#Type:%20jsonobject) `JSON`: The needle properties as JSON
- ??? `AsJSON[`???`]`
- [lgui2brush](#Type:%20lgui2brush) `BackgroundBrush`: Retrieves the Brush for the background of the needle
- [float](#Type:%20float) `Origin`: The Origin used for this specific needle, or NULL if not specified (the Radial Gauges origin is used)
- [float](#Type:%20float) `OuterRadius`: The outer radius (distance from the gauges specified center point) for this needle
- [float](#Type:%20float) `InnerRadius`: The inner radius (distance from the gauges specified center point) for this needle
- [float](#Type:%20float) `OuterRadiusFactor`: The outer radius factor for this needle, as a factor of the radial gauges Actual Outer Radius, to be added to OuterRadius
- [float](#Type:%20float) `InnerRadiusFactor`: The inner radius factor for this needle, as a factor of the radial gauges Actual Outer Radius, to be added to InnerRadius
- [float](#Type:%20float) `ActualOuterRadius`: The actual outer radius, as calculated by (OuterRadiusFactor*RadialGauge.ActualOuterRadius)+OuterRadius
- [float](#Type:%20float) `ActualInnerRadius`: The actual inner radius, as calculated by (InnerRadiusFactor*RadialGauge.ActualOuterRadius)+InnerRadius
- [float](#Type:%20float) `InnerArcLength`: The arc length, in degrees, used for the inner edge of the needle
- [float](#Type:%20float) `OuterArcLength`: The arc length, in degrees, used for the outer edge of the needle
- [int](#Type:%20int) `Value`: The current Value for the needle positioning
- [int](#Type:%20int) `MinValue`: The minimum Value for the needle positioning, or NULL if not specified (the Radial Gauges Range is used)
- [int](#Type:%20int) `MaxValue`: The maximum Value for the needle positioning, or NULL if not specified (the Radial Gauges Range is used)
- [uint](#Type:%20uint) `Segments`: Number of segments (2 triangles each) used to render the needle
- [float](#Type:%20float) `MaxValueArcLength`: The arc length used for the needle position when Value>=MaxValue, in degrees clockwise from Origin, or NULL if not specified (the Radial Gauges MaxValueArcLength is used)

### Methods
- `ApplyStyleJSON[` `json` `]`: Applies a [[LGUI2:Style|Style]] defined by the provided json
- `SetName[` `name` `]`: Sets the Name for the Needle
- `SetBackgroundBrush[` `json` `]`: Sets the [[LGUI2:Brush|Brush]] used for the Needle
- `SetOrigin[` `#` `]`: Sets the Origin used for this specific needle, in degrees clockwise from the top
- `SetOuterRadius[` `#` `]`: Sets the outer radius (distance from the gauges specified center point) for this needle
- `SetInnerRadius[` `#` `]`: Sets the inner radius (distance from the gauges specified center point) for this needle
- `SetOuterRadiusFactor[` `#` `]`: Sets the outer radius factor for this needle, as a factor of the radial gauges Actual Outer Radius, to be added to OuterRadius
- `SetInnerRadiusFactor[` `#` `]`: Sets the inner radius factor for this needle, as a factor of the radial gauges Actual Outer Radius, to be added to InnerRadius
- `SetInnerArcLength[` `#` `]`: Sets the arc length, in degrees, used for the inner edge of the needle
- `SetOuterArcLength[` `#` `]`: Sets the arc length, in degrees, used for the outer edge of the needle
- `SetValue[` `#` `]`: Sets the new current Value for the Needle position
- `SetRange[` `#` `,` `#` `]`: Sets the new minimum and maximum Values for the Needle Range
- `SetSegments[` `#` `]`: Sets the number of segments (2 triangles each) used to render the needle
- `SetMaxValueArcLength[` `#` `]`: Sets the arc length used for the needle position when Value>=MaxValue, in degrees clockwise from Origin
- `Remove`: Removes the Needle from the gauge



## Type: lgui2layer

As Text: Same as `Name`

### Members
- [string](#Type:%20string) `Name`: Name of the layer, such as "base" (the default layer)
- [lgui2screen](#Type:%20lgui2screen) `Screen`: The root element for the layer
- [lgui2hud](#Type:%20lgui2hud) `HUD`: Retrieves the HUD element
- [jsonarray](#Type:%20jsonarray) `KeyboardState`
- [lgui2element](#Type:%20lgui2element) `KeyboardFocusElement`: Retrieves the element with keyboard focus, if any
- [lgui2element](#Type:%20lgui2element) `MouseFocusElement`: Retrieves the element with mouse focus, if any
- ??? `MouseOverElement[`???`]`
- [lgui2element](#Type:%20lgui2element) `MouseCaptureElement`: Retrieves the element with Mouse Capture, if any
- [float](#Type:%20float) `X`: The X coordinate of the top left corner of this layer
- [float](#Type:%20float) `Y`: The Y coordinate of the top left corner of this layer
- [float](#Type:%20float) `Width`: The Width of this layer
- [float](#Type:%20float) `Height`: The Height of this layer
- [float](#Type:%20float) `CursorX`: The X coordinate of the current mouse cursor position
- [float](#Type:%20float) `CursorY`: The Y coordinate of the current mouse cursor position
- [lgui2element](#Type:%20lgui2element) `ElementFromPoint[` `X` `,` `Y` `]`: Retrieves a UI element, given an (X,Y) pair
- [float](#Type:%20float) `FontScale`: A scaling factor to be applied to font sizes for this layer
- [lgui2element](#Type:%20lgui2element) `LoadFile[` `filename` `]`: Loads an [[LGUI2:Element|Element]] file into the layer, returning an [[LGUI2:LS1:lgui2element|lgui2element]]-derived object type depending on the LavishGUI 2 element type. A JSON Object is expected in the file.
- [uint](#Type:%20uint) `LoadArrayFile[` `filename` `]`: Loads a JSON Array file containing [[LGUI2:Element|Elements]] into the layer, returning the number of elements loaded.
- [lgui2element](#Type:%20lgui2element) `LoadJSON[` `json` `]`: Loads an Element, as defined by a json object, into the layer
- ??? `Binding[`???`]`
- ??? `Bindings[`???`]`

### Methods
- `Clear[`???`]`
- `LoadFile[` `filename` `]`: Loads an [[LGUI2:Element|Element]] file into the layer. A JSON Object is expected in the file.
- `LoadArrayFile[` `filename` `]`: Loads a JSON Array file containing [[LGUI2:Element|Elements]] into the layer.
- `LoadJSON[` `json` `]`: Loads an Element, as defined by a json object, into the layer
- `LoadPackageFile[` `filename` `]`: Loads a [[LGUI2:Package|Package]] from file
- `LoadPackageJSON[` `json` `]`: Loads a [[LGUI2:Package|Package]] as defined by a json object
- `AddBinding[` `json` `]`: Adds an [[LGUI2:Input Binding|Input Binding]] to the layer
- `RemoveBinding[` `name` `]`: Removes an [[LGUI2:Input Binding|Input Binding]] from the layer by name
- `LoadBindingsFile[` `filename` `]`: Loads an [[LGUI2:Input Bindings|Input Bindings]] file into the layer. A JSON Array is expected in the file.
- `UnloadFile[`???`]`
- `UnloadArrayFile[`???`]`
- `UnloadJSON[`???`]`
- `UnloadPackageFile[`???`]`
- `UnloadPackageJSON[`???`]`
- `UnloadBindingsFile[`???`]`
- `SetFontScale[` `float` `]`: Sets a new scaling factor to be applied to font sizes for this layer



## Type: lgui2skin

As Text: Same as `Name`

### Members
- [string](#Type:%20string) `Name`: Name of the layer, such as "base" (the default layer)
- [jsonvalue](#Type:%20jsonvalue) `Template[` `templateName` `]`: Retrieves a Template from this Skin, by name
- [jsonvalue](#Type:%20jsonvalue) `TemplateValue[` `templateName` `,` `valueKey` `]`: Retrieves a Templated value from this Skin, given the Template name, and Key to the value
- ??? `Font[`???`]`
- ??? `Brush[`???`]`

### Methods
- `SetTemplate[` `name` `,` `json` `]`: Sets a template within the Skin
- `SetFont[`???`]`
- `SetBrush[`???`]`



## Type: lgui2animationtype

As Text: Same as `Name`

### Members
- [unistring](#Type:%20unistring) `Name`: The name of the Animation Type

### Methods
- `Unregister[`???`]`



## Type: lgui2element

As Text: "lgui2element"

### Members
- [uint](#Type:%20uint) `ID`: The unique ID number of this element
- [unistring](#Type:%20unistring) `Name`: The specified Name (if any) of this element
- [elgui2visibility](#Type:%20elgui2visibility) `Visibility`
- [lgui2layer](#Type:%20lgui2layer) `Layer`: [[LGUI2:Layer|Layer]] containing the element
- [lgui2elementtype](#Type:%20lgui2elementtype) `ElementType`: The type of Element (e.g. "window")
- [bool](#Type:%20bool) `AcceptsKeyboardFocus`: TRUE if the element accepts keyboard focus, allowing non-mouse input events to route to this element
- [bool](#Type:%20bool) `AcceptsMouseFocus`: TRUE if the element accepts mouse focus
- [jsonobject](#Type:%20jsonobject) `Metadata`: The JSON object (if any) containing any Metadata associated with this element
- [jsonobject](#Type:%20jsonobject) `Metadata[` `TRUE` `]`: The JSON object (automatically created if needed) containing any Metadata associated with this element
- [float](#Type:%20float) `X`: X offset for this element
- [float](#Type:%20float) `Y`: Y offset for this element
- [float](#Type:%20float) `XFactor`: X factor for this element
- [float](#Type:%20float) `YFactor`: Y factor for this element
- [float](#Type:%20float) `Width`: Width for this element (does not include Margins)
- [float](#Type:%20float) `WidthFactor`: Width factor for this element (does not include Margins)
- [float](#Type:%20float) `Height`: Height for this element (does not include Margins)
- [float](#Type:%20float) `HeightFactor`: Height factor for this element (does not include Margins)
- [jsonobject](#Type:%20jsonobject) `StorePlacement`: Retrieves a [[LGUI2:Style|Style]] generated with the elements current placement information, including sizing and positioning
- [elgui2horizontalalignment](#Type:%20elgui2horizontalalignment) `HorizontalAlignment`
- [elgui2verticalalignment](#Type:%20elgui2verticalalignment) `VerticalAlignment`
- [float](#Type:%20float) `ActualX`: Actual X position for this element
- [float](#Type:%20float) `ActualY`: Actual Y position for this element
- [float](#Type:%20float) `ActualWidth`: Actual width of this element (does not include Margins)
- [float](#Type:%20float) `ActualHeight`: Actual height of this element (does not include Margins)
- [float](#Type:%20float) `Strata`: A value essentially indicating the visual "priority" of the element, which affects the order of placement and rendering of the element within its parent. In most cases, this affects element Z-Order. 0.0 is considered the normal "bottom" and 1.0 is considered the normal "top", but the range is not specifically limited.
- [lgui2margins](#Type:%20lgui2margins) `Margins`: Margins surrounding this element (outside its bounds)
- [lgui2margins](#Type:%20lgui2margins) `Padding`: Padding surrounding this elements contents (inside its bounds, and border if applicable)
- [float](#Type:%20float) `Opacity`: Opacity value for the element (usually between 0.0 and 1.0, with 1.0 being 100% opaque and 0.0 being fully transparent)
- [lgui2element](#Type:%20lgui2element) `Locate[` `elementName` `,` `elementType` `,` `flags` `]`: [[LGUI2:Locate|Locates]] an element
- [lgui2fontstyle](#Type:%20lgui2fontstyle) `Font`: The [[LGUI2:Font|Font]] used for this element
- [int](#Type:%20int) `Color`: The foreground color value for this element (for convenience, try using Color.Hex)
- [lgui2element](#Type:%20lgui2element) `ContextMenu`: The [[LGUI2:contextmenu|contextmenu]] (if any) for this element
- [bool](#Type:%20bool) `IsKeyboardFocused`: TRUE if the element is Keyboard Focused (relating to AcceptsKeyboardFocus)
- [bool](#Type:%20bool) `IsMouseFocused`: TRUE if the element is the current Mouse Focus element for the Layer
- [bool](#Type:%20bool) `IsMouseOver`: TRUE if the element is the current MouseOver element for the Layer
- [bool](#Type:%20bool) `IsMouseCaptured`: TRUE if the element has captured mouse input, allowing mouse input events to route to this element regardless of MouseOver state
- [lgui2element](#Type:%20lgui2element) `Parent`: The visual parent, if any, of this element
- [lgui2element](#Type:%20lgui2element) `FirstChild`: The first visual child, if any, of this element
- [lgui2element](#Type:%20lgui2element) `LastChild`: The last visual child, if any, of this element
- [lgui2element](#Type:%20lgui2element) `PreviousSibling`: The previous visual sibling, if any, from this element
- [lgui2element](#Type:%20lgui2element) `NextSibling`: The next visual sibling, if any, from this element
- [jsonvalue](#Type:%20jsonvalue) `Style[` `name` `]`: Retrieves a [[LGUI2:Style|Style]] by name
- [lgui2animation](#Type:%20lgui2animation) `Animation[` `name` `]`: Retrieves a loaded [[LGUI2:Animation|Animation]] by name
- [lgui2trigger](#Type:%20lgui2trigger) `Trigger[` `name` `]`: Retrieves a [[LGUI2:Trigger|Trigger]] by name
- ??? `InputHook[`???`]`
- ??? `Tooltip[`???`]`

### Methods
- `SetName[` `value` `]`: Assigns a new value to the Name
- `SetVisibility[` [elgui2visibility](#Type:%20elgui2visibility) `]`
- `SetAcceptsKeyboardFocus[` `bool` `]`: Sets whether the element accepts keyboard focus, allowing non-mouse input events to route to this element
- `SetAcceptsMouseFocus[` `bool` `]`: Sets whether the element accepts mouse focus
- `SetSize[` `#` `,` `#` `]`: Adjusts the requested size of the element (does not include Margins) to the provided Width and Height
- `SetSizeFactor[` `#` `,` `#` `]`: Adjusts the requested size factor of the element (does not include Margins) to the provided Width and Height
- `SetLocation[` `#` `,` `#` `]`: Adjusts the requested location of the element to the provided X and Y
- `SetLocationFactor[` `#` `,` `#` `]`: Adjusts the requested location factor of the element to the provided X and Y
- `SetStrata[` `#` `]`: Sets the Strata value for the element
- `Clear`: Clears/frees element resources, and detaches all children from this element
- `ClearChildren`: Detaches all children from this element
- `Detach`: Detaches this element from its parent (typically for "unloading")
- `Destroy`: A shortcut for :Clear followed by :Detach
- `SetMargins[` `#` `]`: Sets all of this elements margin values to this #
- `SetMargins[` `#` `,` `#` `]`: Sets Left/Right and Top/Bottom margin values to these #s (in that order)
- `SetMargins[` `#` `,` `#` `,` `#` `,` `#` `]`: Sets Left, Top, Right, Bottom margin values to these #s (in that order)
- `SetPadding[` `#` `]`: Sets all of this elements padding values to this #
- `SetPadding[` `#` `,` `#` `]`: Sets Left/Right and Top/Bottom padding values to these #s (in that order)
- `SetPadding[` `#` `,` `#` `,` `#` `,` `#` `]`: Sets Left, Top, Right, Bottom padding values to these #s (in that order)
- `SetHorizontalAlignment[` [elgui2horizontalalignment](#Type:%20elgui2horizontalalignment) `]`
- `SetVerticalAlignment[` [elgui2verticalalignment](#Type:%20elgui2verticalalignment) `]`
- `AddTrigger[` `json` `]`: Adds a [[LGUI2:Trigger|Trigger]] defined by the provided json
- `FireEventHandler[` `name` `]`: Fires a specified Event Handler for the element, with no parameters
- `FireEventHandler[` `name` `,` `json` `]`: Fires a specified Event Handler for the element, passing the given JSON Object
- `FireEventHandler[` `name` `,` `json` `,` [source](#Type:%20source) `element id` `]`: Fires a specified Event Handler for the element, passing the given JSON Object, as from a specified source element
- `SetEventHandler[` `eventName` `,` `json` `]`
- `AddHook[` `eventName` `,` `json` `]`
- `AddInputHook[`???`]`
- `SetContextMenu[` `json` `]`: Sets a new ContextMenu
- `SetOpacity[` `#` `]`: Sets the Opacity value for the element, with 1.0 being opaque and 0.0 being transparent
- `KeyboardFocus[`???`]`
- `CaptureMouse`: Attempts to Capture mouse input, allowing mouse input events to route to this element regardless of MouseOver state
- `ReleaseMouse`: Releases the Captured mouse input, restoring the previous state
- `ApplyStyle[` `name` `]`: Applies a [[LGUI2:Style|Style]] by name
- `ApplyStyleJSON[`???`]`
- `SetStyle[` `name` `,` `json` `]`: Adds a [[LGUI2:Style|Style]] with the provided name to the element
- `RemoveStyle[` `name` `]`: Removes a [[LGUI2:Style|Style]] by name
- `Animate[` `json` `]`: Applies a new [[LGUI2:Animation|Animation]] defined by the provided json
- `SetColor[`???`]`
- `SetFont[`???`]`
- `BubbleToTop`: Bubbles the element to the top of Z-order. This element will be moved over the top of other elements where Strata is less than or equal to its own, and the process will repeat with the elements visual ancestors
- `SetTooltip[`???`]`



## Type: lgui2elementref

As Text: Same as `ID`

### Members
- ??? `ID[`???`]`
- ??? `Element[`???`]`

### Methods
- `Set[`???`]`



## Type: lgui2anchored
- Base Type: [lgui2element](#Type:%20lgui2element)

As Text: "lgui2anchored"

### Members
- ??? `AnchorLocationX[`???`]`
- ??? `AnchorLocationY[`???`]`
- ??? `AnchorLocationFactorX[`???`]`
- ??? `AnchorLocationFactorY[`???`]`
- ??? `AnchorOffsetX[`???`]`
- ??? `AnchorOffsetY[`???`]`
- ??? `AnchorOffsetFactorX[`???`]`
- ??? `AnchorOffsetFactorY[`???`]`
- ??? `ActualAnchorLocationX[`???`]`
- ??? `ActualAnchorLocationY[`???`]`
- ??? `AnchorMode[`???`]`
- ??? `IsClippedToParent[`???`]`

### Methods
- `SetAnchorLocation[`???`]`
- `SetAnchorLocationFactor[`???`]`
- `AnchorToCursor[`???`]`
- `SetAnchorOffset[`???`]`
- `SetAnchorOffsetFactor[`???`]`
- `SetClipToParent[`???`]`



## Type: lgui2bordered
- Base Type: [lgui2element](#Type:%20lgui2element)

As Text: "lgui2bordered"

### Members
- [lgui2margins](#Type:%20lgui2margins) `BorderThickness`: Retrieves the thickness of the border
- [lgui2brush](#Type:%20lgui2brush) `BorderBrush`: Retrieves the Brush for the border itself, if applicable
- [lgui2brush](#Type:%20lgui2brush) `BackgroundBrush`: Retrieves the Brush for the background of the area surrounded by the border, if applicable

### Methods
- `SetBorderThickness[` `#` `]`: Sets all of this elements BorderThickness values to this #
- `SetBorderThickness[` `#` `,` `#` `]`: Sets Left/Right and Top/Bottom BorderThickness values to these #s (in that order)
- `SetBorderThickness[` `#` `,` `#` `,` `#` `,` `#` `]`: Sets Left, Top, Right, Bottom BorderThickness values to these #s (in that order)
- `SetBorderBrush[` `json` `]`
- `SetBackgroundBrush[` `json` `]`



## Type: lgui2contentbase
- Base Type: [lgui2element](#Type:%20lgui2element)

As Text: "lgui2contentbase"

### Members
- [lgui2element](#Type:%20lgui2element) `Content`: Retrieves the Content stored within the Content Container
- [lgui2element](#Type:%20lgui2element) `ContentContainer`: Retrieves the Content Container used to display the Content

### Methods
- `SetContent[` `json` `]`: Sets new Content



## Type: lgui2headeredcontentbase
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2headeredcontentbase"

### Members
- [lgui2element](#Type:%20lgui2element) `Header`: Retrieves the Header stored within the Header Container
- [lgui2element](#Type:%20lgui2element) `HeaderContainer`: Retrieves the Header Container used to display the Content
- [elgui2edge](#Type:%20elgui2edge) `HeaderEdge`: Retrieves the Edge where the Header Container is placed

### Methods
- `SetHeader[` `json` `]`: Sets a new Header
- `SetHeaderEdge[` [elgui2edge](#Type:%20elgui2edge) `]`: Sets the Edge where the Header Container is placed



## Type: lgui2itemlist
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2itemlist"

### Members
- [lgui2element](#Type:%20lgui2element) `ItemsContainer`: The element used to contain and display Item views
- [int64](#Type:%20int64) `ItemCount`: The number of Items contained
- [lgui2item](#Type:%20lgui2item) `Item[` `#` `]`: The item at the given position #
- [int64](#Type:%20int64) `SelectedItemCount`: The number of Items selected
- [lgui2item](#Type:%20lgui2item) `SelectedItem`: The first selected item
- [lgui2item](#Type:%20lgui2item) `SelectedItem[` `#` `]`: The nth selected item
- ??? `ItemsBinding[`???`]`
- ??? `SelectedItemBinding[`???`]`
- ??? `SelectedItemBindingProperty[`???`]`
- ??? `ItemByProperty[`???`]`
- ??? `ItemByValue[`???`]`

### Methods
- `ClearItems`: Clears all Items from the Item List
- `InsertItem[` `json` `]`: Creates a new Item with the given JSON data, inserting it at the end of the Item List
- `InsertItem[` `json` `,` `#` `]`: Creates a new Item with the given JSON data, inserting it at the given position # within the Item List (pushing later items to a higher position #)
- `MoveItem[` `#1` `,` `#2` `]`: Moves the Item from position #1 (removing from this position) to be at position #2 (inserting at this new position)
- `RemoveItem[` `#` `]`: Removes an Item from Item List, at the given position #
- `SetItemSelected[` `#` `,` `TRUE/FALSE` `]`: Sets an Items selected state, at the given position #
- `ClearSelection`: Clears the set of selected Items
- `PushItemsBinding[`???`]`
- `PullItemsBinding[`???`]`
- `PushSelectedItemBinding[`???`]`
- `PullSelectedItemBinding[`???`]`
- `Sort[`???`]`



## Type: lgui2anchor
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2anchor"

### Members
- [float](#Type:%20float) `AnchorX`: X-coordinate to anchor to
- [float](#Type:%20float) `AnchorY`: Y-coordinate to anchor to
- [float](#Type:%20float) `AnchorFactorX`: X Factor to anchor to (as a factor to the visual parents size, e.g. 1.0 being the parents full width)
- [float](#Type:%20float) `AnchorFactorY`: Y Factor to anchor to (as a factor to the visual parents size, e.g. 1.0 being the parents full height)
- ??? `AnchorMode[`???`]`
- [bool](#Type:%20bool) `IsClippedToParent`: TRUE if the anchored element is clipped inside the parent (otherwise, it may leave the parent area)
- [float](#Type:%20float) `AnchorOffsetX`: X-coordinate to offset the anchored element by
- [float](#Type:%20float) `AnchorOffsetY`: Y-coordinate to offset the anchored element by
- [float](#Type:%20float) `AnchorOffsetFactorX`: X Factor to offset the anchored element by (as a factor to the anchored elements size, e.g. 0.5 being the anchored elements center)
- [float](#Type:%20float) `AnchorOffsetFactorY`: Y Factor to offset the anchored element by (as a factor to the anchored elements size, e.g. 0.5 being the anchored elements center)

### Methods
- `SetAnchorLocation[` `#` `,` `#` `]`: Sets a new X,Y location to anchor to
- `SetAnchorLocationFactor[` `#` `,` `#` `]`: Sets a new location factor (X,Y) to anchor to
- `SetAnchorOffset[` `#` `,` `#` `]`: Sets a new X,Y offset for the anchored element
- `SetAnchorOffsetFactor[` `#` `,` `#` `]`: Sets a new X,Y offset factor for the anchored element (as a factor to the anchored elements size, e.g. 0.5,0.5 being the anchored elements center)
- `AnchorToCursor`: Enables anchoring to the cursor location, instead of to the AnchorLocation+AnchorLocationFactor
- `SetClipToParent[` `bool` `]`: Sets whether to clip the anchored element inside the parent (if FALSE, it may leave the parent area)



## Type: lgui2border
- Base Type: [lgui2bordered](#Type:%20lgui2bordered)

As Text: "lgui2border"

### Members
- [...](#Type:%20...) `Child`: The one and only Child element contained by the border
- [elgui2horizontalalignment](#Type:%20elgui2horizontalalignment) `HorizontalContentAlignment`: Horizontal alignment to apply to the Child element
- [elgui2verticalalignment](#Type:%20elgui2verticalalignment) `VerticalContentAlignment`: Vertical alignment to apply to the Child element
- ??? `MaintainAspectRatio[`???`]`

### Methods
- `SetChild[` `json` `]`
- `SetHorizontalContentAlignment[` [elgui2horizontalalignment](#Type:%20elgui2horizontalalignment) `]`: New horizontal alignment to apply to the Child element
- `SetVerticalContentAlignment[` [elgui2verticalalignment](#Type:%20elgui2verticalalignment) `]`: New vertical alignment to apply to the Child element
- `SetMaintainAspectRatio[`???`]`



## Type: lgui2button
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2button"

### Members
- [bool](#Type:%20bool) `Pressed`: TRUE if the button is currently pressed

### Methods
- `SetPressed[` `TRUE/FALSE` `]`: Sets a new pressed state
- `TogglePressed`: Toggles the pressed state



## Type: lgui2sensitivebutton
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2sensitivebutton"

### Members
- ??? `Value[`???`]`
- ??? `ValueBinding[`???`]`

### Methods
- `SetValue[`???`]`
- `PullValueBinding[`???`]`
- `PushValueBinding[`???`]`



## Type: lgui2knob
- Base Type: [lgui2element](#Type:%20lgui2element)

As Text: "lgui2knob"

### Members
- ??? `Value[`???`]`
- ??? `ValueBinding[`???`]`

### Methods
- `SetValue[`???`]`
- `PullValueBinding[`???`]`
- `PushValueBinding[`???`]`



## Type: lgui2canvas

As Text: "lgui2canvas"

### Members
- [lgui2fontstyle](#Type:%20lgui2fontstyle) `Font[` `name` `]`: Retrieves one of the Canvass Fonts, by name
- [lgui2brush](#Type:%20lgui2brush) `Brush[` `name` `]`: Retrieves one of the Canvass Brushes, by name
- ??? `CanvasHeight[`???`]`
- ??? `CanvasWidth[`???`]`
- ??? `CanvasRenderer[`???`]`

### Methods
- `ClearCanvas`: Clears the Canvas, setting all pixels to transparent #00000000
- `ClearCanvas[` `#aarrggbb` `]`: Clears the Canvas to the specified color
- `InitializeCanvas`: Initializes the Canvas by Batching its "initialize" array, if it has not been auto-initialized since last allocated. (This call should not usually be needed)
- `InitializeCanvas[` `TRUE` `]`: Initializes the Canvas by Batching its "initialize" array, even if it has already been auto-initialized. This may be useful after a ClearCanvas
- `SetCanvasSize[`???`]`
- `Reset`: Removes the "initialize" array and resets the Brush and Font stacks, but does not automatically clear the canvas or remove Brush and Font definitions.
- `SetFont[` `name` `,` `json` `]`: Sets the Canvass font for the given name to a specified [[LGUI2:Font|Font definition]]
- `SetBrush[` `name` `,` `json` `]`: Sets the Canvass brush for the given name to a specified [[LGUI2:Brush|Brush definition]]
- `PushFont[` `name` `]`: Pushes one of the Canvass defined Fonts onto the stack by name
- `PushBrush[` `name` `]`: Pushes one of the Canvass defined Brushes onto the stack by name
- `PopBrush`: Pops a Brush off the stack
- `PopBrush[` `name` `]`: Pops a Brush off the stack, if and only if it is the specified brush
- `PopFont`: Pops a Font off the stack
- `PopFont[` `name` `]`: Pops a Font off the stack, if and only if it is the specified font
- `DrawRect[` `json` `]`: Performs one "drawRect" [[LGUI2:Canvas Operation|Canvas Operation]]
- `DrawText[` `json` `]`: Performs one "drawText" [[LGUI2:Canvas Operation|Canvas Operation]]
- `DrawCircle[` `json` `]`: Performs one "drawCircle" [[LGUI2:Canvas Operation|Canvas Operation]]
- `DrawArc[` `json` `]`: Performs one "drawArc" [[LGUI2:Canvas Operation|Canvas Operation]]
- `DrawPrimitives[` `json` `]`: Performs one "drawPrimitives" [[LGUI2:Canvas Operation|Canvas Operation]] (rendering any number of vertices)
- `PushTransform[`???`]`
- `SetTransform[`???`]`
- `PopTransform[`???`]`
- `PushBlendMode[`???`]`
- `PopBlendMode[`???`]`
- `Batch[` `jsonarray` `]`: Performs an array of [[LGUI2:Canvas Operations|Canvas Operations]]



## Type: lgui2checkbox
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2checkbox"

### Members
- [bool](#Type:%20bool) `Checked`: TRUE if checked, FALSE if not checked, or NULL if Indeterminate
- ??? `CheckedBinding[`???`]`

### Methods
- `SetChecked[` `newValue` `]`
- `PullCheckedBinding[`???`]`
- `PushCheckedBinding[`???`]`



## Type: lgui2dragger
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2dragger"

### Members
- [bool](#Type:%20bool) `AllowMove`: TRUE if the dragger is allowed to be moved
- [bool](#Type:%20bool) `AllowResize`: TRUE if the dragger is allowed to be resized

### Methods
- `SetAllowMove[` `TRUE/FALSE` `]`: Sets a new AllowMove value
- `SetAllowResize[` `TRUE/FALSE` `]`: Sets a new AllowResize value



## Type: lgui2expander
- Base Type: [lgui2headeredcontentbase](#Type:%20lgui2headeredcontentbase)

As Text: "lgui2expander"

### Members
- [bool](#Type:%20bool) `Expanded`: TRUE if the content is expanded

### Methods
- `SetExpanded[` `TRUE/FALSE` `]`: Sets a new Expanded state
- `ToggleExpanded`: Toggles the Expanded state, regardless of the current value



## Type: lgui2imagebox
- Base Type: [lgui2bordered](#Type:%20lgui2bordered)

As Text: "lgui2imagebox"

### Members
- [lgui2brush](#Type:%20lgui2brush) `ImageBrush`: The [[LGUI2:Brush|Brush]] used for the subject of the imagebox
- [bool](#Type:%20bool) `ScaleToFit`: TRUE if the image should be scaled to fit

### Methods
- `SetImageBrush[` `json` `]`: Sets a new [[LGUI2:Brush|Brush]] for the imagebox
- `SetScaleToFit[` `TRUE/FALSE` `]`: Sets a new ScaleToFit value



## Type: lgui2inputpicker
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2inputpicker"

### Members
- ??? `Value[`???`]`
- ??? `ValueBinding[`???`]`
- ??? `IsMultipleControlMode[`???`]`
- ??? `Summary[`???`]`

### Methods
- `SetMultipleControlMode[`???`]`
- `SetValue[`???`]`
- `PullValueBinding[`???`]`
- `PushValueBinding[`???`]`



## Type: lgui2listbox
- Base Type: [lgui2itemlist](#Type:%20lgui2itemlist)

As Text: "lgui2listbox"

### Members
none.
### Methods
none.


## Type: lgui2objectview
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2objectview"

### Members
- ??? `Object[`???`]`
- ??? `Property[`???`]`
- ??? `PropertyNames[`???`]`

### Methods
- `ClearProperties[`???`]`
- `AddProperty[`???`]`
- `RemoveProperty[`???`]`



## Type: lgui2property

As Text: "lgui2property"

### Members
- ??? `Name[`???`]`
- ??? `ObjectView[`???`]`
- ??? `Object[`???`]`
- ??? `View[`???`]`

### Methods
none.


## Type: lgui2propertyview
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2propertyview"

### Members
- ??? `Property[`???`]`
- ??? `ObjectView[`???`]`
- ??? `Object[`???`]`
- ??? `Value[`???`]`
- ??? `ValueBinding[`???`]`

### Methods
- `SetValue[`???`]`



## Type: lgui2itemview
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2itemview"

### Members
- [lgui2itemlist](#Type:%20lgui2itemlist) `ItemList`: The lgui2itemlist containing the Item
- [lgui2item](#Type:%20lgui2item) `Item`: The lgui2item responsible for this view

### Methods
none.


## Type: lgui2combobox
- Base Type: [lgui2listbox](#Type:%20lgui2listbox)

As Text: "lgui2combobox"

### Members
- ??? `Header[`???`]`
- ??? `HeaderContainer[`???`]`
- ??? `HeaderEdge[`???`]`
- [bool](#Type:%20bool) `Open`: TRUE if the combobox drop-down is open

### Methods
- `SetHeaderEdge[`???`]`
- `SetHeader[`???`]`
- `SetOpen[` `TRUE/FALSE` `]`: Sets a new Open state
- `ToggleOpen`: Toggles the Open state



## Type: lgui2panel
- Base Type: [lgui2bordered](#Type:%20lgui2bordered)

As Text: "lgui2panel"

### Members
- [...](#Type:%20...) `AddChild[` `json` `]`: Adds a child element to the panel, and returns the element

### Methods
- `AddChild[` `json` `]`: Adds a child element to the panel



## Type: lgui2popup
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2popup"

### Members
- [bool](#Type:%20bool) `Open`: Retrieves the current Open state for the popup

### Methods
- `SetOpen[` `TRUE/FALSE` `]`: Sets a new Open state for the popup
- `SetOpen[` `TRUE` `,` `x` `,` `y` `]`: Sets a new Open state for the popup, using the provided (x,y) location if it is TRUE
- `ToggleOpen`: Toggles the Open state for the popup
- `ToggleOpen[` `x` `,` `y` `]`: Toggles the Open state for the popup, using the provided (x,y) location if it is changing to TRUE



## Type: lgui2progressbar
- Base Type: [lgui2bordered](#Type:%20lgui2bordered)

As Text: "lgui2progressbar"

### Members
- [int](#Type:%20int) `Value`: The current value from the progressbar
- [int](#Type:%20int) `MinValue`: The minimum progressbar value
- [int](#Type:%20int) `MaxValue`: The maximum progressbar value
- [lgui2brush](#Type:%20lgui2brush) `FillerBrush`: The [[LGUI2:Brush|Brush]] used for the progress bar filler
- [lgui2brush](#Type:%20lgui2brush) `OverlayBrush`: The [[LGUI2:Brush|Brush]] used for an overlay (usually partly transparent) over the progress bar filler
- [elgui2edge](#Type:%20elgui2edge) `FillFromEdge`: The edge to begin filling from
- [elgui2progresstext](#Type:%20elgui2progresstext) `ProgressText`: The style of progress text, if any, to show on the bar
- ??? `ValueBinding[`???`]`

### Methods
- `SetValue[` `#` `]`: Set a new value for the slider
- `SetRange[` `min` `,` `max` `]`: Set new minimum and maximum values for the progressbar
- `SetFillFromEdge[` `newValue` `]`
- `SetProgressText[` `newValue` `]`
- `SetFillerBrush[` `json` `]`
- `SetOverlayBrush[` `json` `]`
- `PullValueBinding[`???`]`
- `PushValueBinding[`???`]`



## Type: lgui2radialgauge
- Base Type: [lgui2bordered](#Type:%20lgui2bordered)

As Text: "lgui2radialgauge"

### Members
- [float](#Type:%20float) `Origin`: Where the radial layout begins, in degrees clockwise from top. 0.0 &lt;= value &lt; 360.0
- [uint](#Type:%20uint) `Resolution`: The number of edges used to render the perimeter of a 360-degree FillerBrush circle. For optimal performance, use the lowest value that still looks good at the desired size
- [float](#Type:%20float) `MaxValueArcLength`: The full arc length, in degrees clockwise from Origin, when Value>=MaxValue -- default is 360.0
- [int](#Type:%20int) `Value`: The current Value for the FillerBrush
- [int](#Type:%20int) `MinValue`: The minimum Value for the FillerBrush Range
- [int](#Type:%20int) `MaxValue`: The maximum Value for the FillerBrush Range
- [lgui2brush](#Type:%20lgui2brush) `FillerBrush`: The [[LGUI2:Brush|Brush]] used to render the Filler arc
- [lgui2brush](#Type:%20lgui2brush) `OverlayBrush`: The [[LGUI2:Brush|Brush]] used to render the Overlay after rendering the Filler and any Needles
- [elgui2progresstext](#Type:%20elgui2progresstext) `ProgressText`: The style of progress text, if any, to show on the bar
- [float](#Type:%20float) `OuterRadius`: The radius from the CenterPoint to the outer edge of the FillerBrush -- default is 0.0
- [float](#Type:%20float) `OuterRadiusFactor`: The radius factor, as a factor of the inner size (excluding padding and border) of the radialgauge, to add to OuterRadius -- default is 0.5
- [float](#Type:%20float) `ActualOuterRadius`: The actual outer radius, as calculated by (OuterRadiusFactor*Size)+OuterRadius, where Size is the smaller between the radial gauges Width and Height
- [float](#Type:%20float) `InnerRadius`: The radius from the CenterPoint to the inner edge of the FillerBrush -- default is 0.0
- [float](#Type:%20float) `InnerRadiusFactor`: The radius factor, as a factor of the inner size (excluding padding and border) of the radialgauge, to add to InnerRadius -- default is 0.0
- [float](#Type:%20float) `ActualInnerRadius`: The actual inner radius, as calculated by (InnerRadiusFactor*Size)+InnerRadius, where Size is the smaller between the radial gauges Width and Height
- [float](#Type:%20float) `CenterPointX`: The X coordinate of the point to use as the center for the FillerBrush and any Needles -- default is 0.0
- [float](#Type:%20float) `CenterPointY`: The Y coordinate of the point to use as the center for the FillerBrush and any Needles -- default is 0.0
- [float](#Type:%20float) `CenterPointXFactor`: The X Factor (as a factor of the actual width of the radialgauge) of the point to use as the center for the FillerBrush and any Needles -- default is 0.5
- [float](#Type:%20float) `CenterPointYFactor`: The Y Factor (as a factor of the actual height of the radialgauge) of the point to use as the center for the FillerBrush and any Needles -- default is 0.5
- [uint](#Type:%20uint) `NeedleCount`: The number of Needles
- [lgui2radialgaugeneedle](#Type:%20lgui2radialgaugeneedle) `Needle[` `#` `]`: The n-th Needle (1-based) if any
- ??? `ValueBinding[`???`]`

### Methods
- `SetOrigin[` `#` `]`: Sets where the radial layout begins, in degrees clockwise from top. This value will automatically adjust into the range 0.0 &lt;= value &lt; 360.0, meaning -1 becomes 359, and 361 becomes 1.
- `SetResolution[` `#` `]`: Sets the number of edges used to render the perimeter of a 360-degree FillerBrush circle. For optimal performance, use the lowest value that still looks good at the desired size
- `SetMaxValueArcLength[` `#` `]`: Sets the full arc length, in degrees clockwise from Origin, when Value>=MaxValue
- `SetValue[` `#` `]`: Sets the new current Value for the FillerBrush
- `SetRange[` `#` `,` `#` `]`: Sets the new minimum and maximum Values for the FillerBrush Range
- `SetFillerBrush[` `json` `]`: Sets the [[LGUI2:Brush|Brush]] used to render the Filler arc
- `SetOverlayBrush[` `json` `]`: Sets the [[LGUI2:Brush|Brush]] used to render the Overlay after rendering the Filler and any Needles
- `SetProgressText[` `newValue` `]`: Sets the style of progress text, if any, to show on the bar. Must be a valid [[LGUI2:LS1:elgui2progresstext|elgui2progresstext]] value
- `SetOuterRadius[` `#` `]`: Sets the radius from the CenterPoint to the outer edge of the FillerBrush -- default is 0.0
- `SetOuterRadiusFactor[` `#` `]`: Sets the radius factor, as a factor of the inner size (excluding padding and border) of the radialgauge, to add to OuterRadius -- default is 0.5
- `SetInnerRadius[` `#` `]`: Sets the radius from the CenterPoint to the inner edge of the FillerBrush -- default is 0.0
- `SetInnerRadiusFactor[` `#` `]`: Sets the radius factor, as a factor of the inner size (excluding padding and border) of the radialgauge, to add to InnerRadius -- default is 0.0
- `SetCenterPoint[` `#` `,` `#` `]`: Sets the point to use as the center for the FillerBrush and any Needles -- default is 0,0
- `SetCenterPointFactor[` `#` `,` `#` `]`: Sets the X,Y Factor  (as a factor of the actual width and height of the radialgauge) of the point to use as the center for the FillerBrush and any Needles -- default is 0.5,0.5
- `SetNeedle[` `name` `,` `json` `]`: Sets a Needle with the specified name, with a [[LGUI2:radialgaugeneedle|radialgaugeneedle]] definition. If a Needle already exists with the given name, it is removed
- `ClearNeedles`: Clears all Needles
- `PushValueBinding[`???`]`
- `PullValueBinding[`???`]`



## Type: lgui2radialpanel
- Base Type: [lgiu2panel](#Type:%20lgiu2panel)

As Text: "lgui2radialpanel"

### Members
- [float](#Type:%20float) `DeadZone`: The radius of the Dead Zone in the center of the panel
- [float](#Type:%20float) `LiveZone`: The radius of the Live Zone, the default size for added Radial Items
- [float](#Type:%20float) `ZoneMargin`: The distance between the Dead Zone and Live Zone
- [float](#Type:%20float) `Origin`: Where the radial layout begins, in degrees clockwise from top. 0.0 &lt;= value &lt; 360.0
- [uint](#Type:%20uint) `Resolution`: The number of edges used to render the perimeter of the circle. For optimal performance, use the lowest value that still looks good at the desired size
- [float](#Type:%20float) `ChildWidth`: Width reserved for child elements
- [float](#Type:%20float) `ChildHeight`: Height reserved for child elements
- [lgui2radialitem](#Type:%20lgui2radialitem) `RadialItemByElement[` `#` `]`: Retrieves a [[LGUI2:Radial Item|Radial Item]] from a Child elements ID
- [lgui2radialitem](#Type:%20lgui2radialitem) `RadialItemByVector[` `degreesClockwise` `,` `distance` `]`: Retrieves the [[LGUI2:Radial Item|Radial Item]], if any, at a specified angle and distance from the center
- [lgui2radialitem](#Type:%20lgui2radialitem) `RadialItemByPoint[` `#` `,` `#` `]`: Retrieves the [[LGUI2:Radial Item|Radial Item]], if any, at a specified X,Y location (relative to the Layer, i.e. the game window)
- [lgui2radialitem](#Type:%20lgui2radialitem) `MouseOverItem`: Retrieves the Radial Item that falls under the mouse cursor
- [jsonobject](#Type:%20jsonobject) `RadialItemTemplate`: The base template used for Radial Items added to this panel
- [lgui2brush](#Type:%20lgui2brush) `DeadZoneBrush`: The [[LGUI2:Brush|Brush]] used to render the Dead Zone in the center of the panel

### Methods
- `SetDeadZone[` `#` `]`: Sets the radius of the Dead Zone in the center of the panel
- `SetChildSize[` `#` `]`: Sets the reserved size for child elements to a square of this size
- `SetChildSize[` `#` `,` `#` `]`: Sets the reserved size for child elements to the provided Width and Height
- `SetRadialItemTemplate[` `json` `]`: Sets the base template used for Radial Items added to this panel
- `SetLiveZone[` `#` `]`: Sets the radius of the Live Zone, the default size for added Radial Items
- `SetZoneMargin[` `#` `]`: Sets the distance between the Dead Zone and Live Zone
- `SetOrigin[` `#` `]`: Sets where the radial layout begins, in degrees clockwise from top. This value will automatically adjust into the range 0.0 &lt;= value &lt; 360.0, meaning -1 becomes 359, and 361 becomes 1.
- `SetResolution[` `#` `]`: Sets the number of edges used to render the perimeter of the circle. For optimal performance, use the lowest value that still looks good at the desired size
- `SetDeadZoneBrush[` `json` `]`: Sets the [[LGUI2:Brush|Brush]] used to render the Dead Zone in the center of the panel



## Type: lgui2screen
- Base Type: [lgui2element](#Type:%20lgui2element)

As Text: "lgui2screen"

### Members
none.
### Methods
none.


## Type: lgui2scrollviewer
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2scrollviewer"

### Members
- [float](#Type:%20float) `ViewOffsetX`: The scrolled offset, in pixels, of the views top left corner
- [float](#Type:%20float) `ViewOffsetY`: The scrolled offset, in pixels, of the views top left corner
- [float](#Type:%20float) `MaxViewExtentsWidth`: Maximum scrollable width of the viewed contents, or -1 for automatic
- [float](#Type:%20float) `MaxViewExtentsHeight`: Maximum scrollable height of the viewed contents, or -1 for automatic
- [float](#Type:%20float) `MinViewExtentsWidth`: Minimum scrollable width of the viewed contents
- [float](#Type:%20float) `MinViewExtentsHeight`: Minimum scrollable height of the viewed contents
- [float](#Type:%20float) `ActualViewExtentsWidth`: Actual scrollable width of the viewed contents
- [float](#Type:%20float) `ActualViewExtentsHeight`: Actual scrollable height of the viewed contents

### Methods
- `SetViewOffset[` `x` `,` `y` `]`: Sets the scrolled offset, in pixels, of the views top left corner
- `SetMinViewExtents[` `width` `,` `height` `]`: Sets the minimum scrollable extents for the viewed contents
- `SetMaxViewExtents[` `width` `,` `height` `]`: Sets the maximum scrollable extents for the viewed contents



## Type: lgui2slider
- Base Type: [lgui2bordered](#Type:%20lgui2bordered)

As Text: "lgui2slider"

### Members
- [int](#Type:%20int) `Value`: The current value from the slider
- [int](#Type:%20int) `MinValue`: The minimum slider value
- [int](#Type:%20int) `MaxValue`: The maximum slider value
- [lgui2element](#Type:%20lgui2element) `Handle`: The sliders handle
- [elgui2edge](#Type:%20elgui2edge) `SlideFromEdge`: The edge the slider begins sliding from
- ??? `ValueBinding[`???`]`

### Methods
- `SetValue[` `#` `]`: Sets a new Value for the slider
- `SetRange[` `#` `,` `#` `]`
- `SetSlideFromEdge[` [elgui2edge](#Type:%20elgui2edge) `]`: Sets the edge the slider begins sliding from
- `PullValueBinding[`???`]`
- `PushValueBinding[`???`]`



## Type: lgui2dockpanel
- Base Type: [lgui2panel](#Type:%20lgui2panel)

As Text: "lgui2dockpanel"

### Members
none.
### Methods
none.


## Type: lgui2hud
- Base Type: [lgui2contentbase](#Type:%20lgui2contentbase)

As Text: "lgui2hud"

### Members
- [lgui2element](#Type:%20lgui2element) `IndicatorIconContainer`
- [lgui2element](#Type:%20lgui2element) `NotificationIconContainer`
- [lgui2element](#Type:%20lgui2element) `TooltipContainer`
- [lgui2element](#Type:%20lgui2element) `TooltipOwner`
- [lgui2item](#Type:%20lgui2item) `AddIndicatorIcon[` `json` `]`
- [lgui2item](#Type:%20lgui2item) `AddNotificationIcon[` `json` `]`

### Methods
- `AddIndicatorIcon[` `json` `]`
- `RemoveIndicatorIcon[`???`]`
- `AddNotificationIcon[` `json` `]`
- `RemoveNotificationIcon[`???`]`
- `SetTooltip[` `element` `,` `x` `,` `y` `,` `json` `]`: Sets the active tooltip
- `UnsetTooltip[` `element` `]`: Un-sets (deactivates) the active tooltip



## Type: lgui2scrollbar
- Base Type: [lgui2dockpanel](#Type:%20lgui2dockpanel)

As Text: "lgui2scrollbar"

### Members
- [int](#Type:%20int) `Value`: The current value from the scrollbar
- [int](#Type:%20int) `MinValue`: The minimum scrollbar value
- [int](#Type:%20int) `MaxValue`: The maximum scrollbar value
- [int](#Type:%20int) `Increment`: Amount to adjust the current value per Mouse Wheel tick
- [int](#Type:%20int) `PageIncrement`: Amount to adjust the current value per Page Up/Down
- ??? `ValueBinding[`???`]`

### Methods
- `IncValue[`???`]`
- `SetValue[` `#` `]`: Sets a new Value for the scrollbar
- `SetRange[` `#` `,` `#` `]`
- `SetIncrement[` `#` `]`: Sets a new Increment value
- `SetPageIncrement[` `#` `]`: Sets a new PageIncrement value
- `PullValueBinding[`???`]`
- `PushValueBinding[`???`]`



## Type: lgui2stackpanel
- Base Type: [lgui2panel](#Type:%20lgui2panel)

As Text: "lgui2stackpanel"

### Members
- [bool](#Type:%20bool) `Horizontal`
- [bool](#Type:%20bool) `Uniform`
- ??? `Reversed[`???`]`
- [elgui2horizontalalignment](#Type:%20elgui2horizontalalignment) `HorizontalContentAlignment`
- [elgui2verticalalignment](#Type:%20elgui2verticalalignment) `VerticalContentAlignment`

### Methods
- `SetHorizontal[` `TRUE/FALSE` `]`
- `SetUniform[` `TRUE/FALSE` `]`
- `SetReversed[` `TRUE/FALSE` `]`
- `SetHorizontalContentAlignment[` `newValue` `]`
- `SetVerticalContentAlignment[` `newValue` `]`



## Type: lgui2treepanel
- Base Type: [lgui2stackpanel](#Type:%20lgui2stackpanel)

As Text: "lgui2treepanel"

### Members
none.
### Methods
none.


## Type: lgui2contextmenu
- Base Type: [lgui2itemlist](#Type:%20lgui2itemlist)

As Text: "lgui2contextmenu"

### Members
- [bool](#Type:%20bool) `Open`: TRUE if the Context Menu is currently open

### Methods
- `Open[` `x` `,` `y` `]`: Open the Context Menu at the given (x,y) location
- `Close`: Closes the Context Menu



## Type: lgui2tab
- Base Type: [lgui2headeredcontentbase](#Type:%20lgui2headeredcontentbase)

As Text: "lgui2tab"

### Members
- ??? `IsSelected[`???`]`
- ??? `TabControl[`???`]`

### Methods
- `Select[`???`]`



## Type: lgui2tabcontrol
- Base Type: [lgui2headeredcontentbase](#Type:%20lgui2headeredcontentbase)

As Text: "lgui2tabcontrol"

### Members
- [LS1:lgui2tab](#Type:%20LS1:lgui2tab) `SelectedTab`: The currently selected [[LGUI2:tab|tab]]
- [LS1:lgui2tab](#Type:%20LS1:lgui2tab) `Tab[` `#` `]`: The #th tab
- [int64](#Type:%20int64) `Tabs`: Number of tabs

### Methods
- `SelectTab[` `#` `]`: Selects the #th tab
- `AddTab[` `json` `]`: Adds a tab, given a JSON object defining a [[LGUI2:tab|tab]] element
- `RemoveTab[`???`]`



## Type: lgui2textblock
- Base Type: [lgui2element](#Type:%20lgui2element)

As Text: "lgui2textblock"

### Members
- [string](#Type:%20string) `Text`: The text contained in the textblock
- [bool](#Type:%20bool) `Wrap`: TRUE if the text should be wrapped to additional lines in order to fit
- ??? `HorizontalContentAlignment[`???`]`
- ??? `VerticalContentAlignment[`???`]`
- ??? `TextBinding[`???`]`

### Methods
- `SetText[` `text` `]`: Sets a new Text value
- `SetWrap[` `bool` `]`: Sets a new Wrap value
- `SetHorizontalContentAlignment[`???`]`
- `SetVerticalContentAlignment[`???`]`
- `PushTextBinding[`???`]`
- `PullTextBinding[`???`]`



## Type: lgui2textbox
- Base Type: [lgui2bordered](#Type:%20lgui2bordered)

As Text: "lgui2textbox"

### Members
- [string](#Type:%20string) `Text`: The text contained in the textbox
- [bool](#Type:%20bool) `Wrap`: TRUE if the text should be wrapped to additional lines in order to fit
- [bool](#Type:%20bool) `Multiline`: TRUE if the textbox allows multiple lines of text
- ??? `TextBinding[`???`]`

### Methods
- `SetText[` `text` `]`: Sets a new Text value
- `SetWrap[` `bool` `]`: Sets a new Wrap value
- `SetMultiline[` `bool` `]`: Sets a new Multiline value
- `PushTextBinding[`???`]`
- `PullTextBinding[`???`]`



## Type: lgui2commandbox
- Base Type: [lgui2textbox](#Type:%20lgui2textbox)

As Text: "lgui2commandbox"

### Members
none.
### Methods
none.


## Type: lgui2window
- Base Type: [lgui2headeredcontentbase](#Type:%20lgui2headeredcontentbase)

As Text: "lgui2window"

### Members
- [bool](#Type:%20bool) `Shade`: TRUE if the window is shaded ("minimized" in place but shown as the header)
- [elgui2sizetocontent](#Type:%20elgui2sizetocontent) `SizeToContent`
- [bool](#Type:%20bool) `HideOnClose`: TRUE if the window should Hide instead of Close (and no longer exist), when the Close button is clicked
- ??? `AnchorLocationX[`???`]`
- ??? `AnchorLocationY[`???`]`
- ??? `AnchorLocationFactorX[`???`]`
- ??? `AnchorLocationFactorY[`???`]`
- ??? `AnchorOffsetX[`???`]`
- ??? `AnchorOffsetY[`???`]`
- ??? `AnchorOffsetFactorX[`???`]`
- ??? `AnchorOffsetFactorY[`???`]`
- ??? `ActualAnchorLocationX[`???`]`
- ??? `ActualAnchorLocationY[`???`]`
- ??? `IsHeightResizable[`???`]`
- ??? `IsWidthResizable[`???`]`
- ??? `AnchorMode[`???`]`
- ??? `IsClippedToParent[`???`]`

### Methods
- `SetShade[` `TRUE/FALSE` `]`: Sets a new Shade state
- `ToggleShade`: Toggles the Shade state, regardless of the current value
- `SetSizeToContent[` [elgui2sizetocontent](#Type:%20elgui2sizetocontent) `]`
- `SetHideOnClose[` `TRUE/FALSE` `]`: Sets a new HideOnClose state
- `SetAnchorLocation[`???`]`
- `SetAnchorLocationFactor[`???`]`
- `AnchorToCursor[`???`]`
- `SetHeightResizable[`???`]`
- `SetWidthResizable[`???`]`
- `SetAnchorOffset[`???`]`
- `SetAnchorOffsetFactor[`???`]`
- `SetClipToParent[`???`]`



## Type: lgui2wrappanel
- Base Type: [lgui2stackpanel](#Type:%20lgui2stackpanel)

As Text: "lgui2wrappanel"

### Members
- ??? `ChildHeight[`???`]`
- ??? `ChildWidth[`???`]`

### Methods
- `SetChildSize[`???`]`



## Type: lgui2table
- Base Type: [lgui2panel](#Type:%20lgui2panel)

As Text: "lgui2table"

### Members
- ??? `NumRows[`???`]`
- ??? `NumColumns[`???`]`
- ??? `CellSpacingWidth[`???`]`
- ??? `CellSpacingHeight[`???`]`
- ??? `CellSpacingWidthFactor[`???`]`
- ??? `CellSpacingHeightFactor[`???`]`
- ??? `RowHeight[`???`]`
- ??? `RowHeightFactor[`???`]`
- ??? `ColumnWidth[`???`]`
- ??? `ColumnWidthFactor[`???`]`
- ??? `AutoFillFirstRow[`???`]`
- ??? `AutoFillLastRow[`???`]`
- ??? `AutoFillFirstColumn[`???`]`
- ??? `AutoFillLastColumn[`???`]`
- ??? `GetElementCell[`???`]`
- ??? `GetCellElement[`???`]`
- ??? `Rows[`???`]`
- ??? `Columns[`???`]`

### Methods
- `SetCellSpacing[`???`]`
- `SetCellSpacingFactor[`???`]`
- `SetRow[`???`]`
- `SetColumn[`???`]`
- `SetAutoFillRows[`???`]`
- `SetAutoFillColumns[`???`]`
- `SetRows[`???`]`
- `SetColumns[`???`]`



## Type: lgui2page
- Base Type: [lgui2tab](#Type:%20lgui2tab)

As Text: "lgui2page"

### Members
- ??? `PageControl[`???`]`

### Methods
none.


## Type: lgui2pagecontrol
- Base Type: [lgui2tabcontrol](#Type:%20lgui2tabcontrol)

As Text: "lgui2pagecontrol"

### Members
- ??? `SelectedPage[`???`]`
- ??? `Page[`???`]`
- ??? `Pages[`???`]`

### Methods
- `SelectPage[`???`]`
- `AddPage[`???`]`
- `RemovePage[`???`]`



Inner Space Kernel API Specification (LavishScript)

---
# Events
## Event: LavishVM Frame Ends

## Event: OnFrame

## Event: OnMouseEnter

## Event: OnMouseExit

## Event: OnConsoleLine

## Event: OnConsoleLineStripped

## Event: OnButtonDown

## Event: OnButtonUp

## Event: OnButtonMove

## Event: OnAxisMove

## Event: OnDPadMove

## Event: OnMouseMove

## Event: OnMouseWheel

## Event: OnButtonDownLastChance

## Event: OnButtonUpLastChance

## Event: OnButtonMoveLastChance

## Event: OnMouseWheelLastChance


---
# Commands
## Command: Version
### Syntax
* `Version`

## Command: ConsoleClear
### Syntax
* `ConsoleClear`

## Command: ConsoleRedirect
### Syntax
* `ConsoleRedirect` <[string](#Type:%20string) `LGUIconsoleFQN`> <... [string](#Type:%20string) `command`>

## Command: Exit
### Syntax
* `Exit`

## Command: Gamma
### Syntax
* `Gamma` "-reset"|"-store"|"-display"|"-restore"
* `Gamma` "-inc"|"-dec"|"-set" <[uint](#Type:%20uint) `newLevel`>

## Command: FPS
### Syntax
* `FPS`

## Command: DisplayInfo
### Syntax
* `DisplayInfo`

## Command: GlobalKey
### Syntax
* `GlobalKey` "-keylist"|"-list"
* `GlobalKey` "-clear" [[string](#Type:%20string) `key`]
* `GlobalKey` <[string](#Type:%20string) `key`>

## Command: Services

## Command: GlobalBind
### Syntax
* `GlobalBind` "-list"|"-clear"
* `GlobalBind` "-delete" <[string](#Type:%20string) `name`>
* `GlobalBind` <[string](#Type:%20string) `name`> <[string](#Type:%20string) `keyCombo`> <... [string](#Type:%20string) `command`>

## Command: PlaySound
### Syntax
* `PlaySound` <[string](#Type:%20string) `filename`>
* `PlaySound` "on"|"off"
* `PlaySound` "SystemAsterisk"|"SystemDefault"|"SystemExclamation"|"SystemExit"|"SystemHand"|"SystemQuestion"|"SystemStart"|"SystemWelcome"

## Command: Log
### Syntax
* `Log` <[string](#Type:%20string) `filename`>
* `Log` "off"

## Command: MaxFPS
### Syntax
* `MaxFPS`
* `MaxFPS`
* `MaxFPS`
* `MaxFPS`

## Command: XMLSetting

## Command: HTTPGet
### Syntax
* `HTTPGet` ["-postparam"] ["-postfile"] ["-atom"] ["-file"] <[string](#Type:%20string) `url`>

## Command: Diagnostics
### Syntax
* `Diagnostics`

## Command: Relay
### Syntax
* `Relay` <[string](#Type:%20string) `target`> "-echo" <... [string](#Type:%20string) `message`>
* `Relay` <[string](#Type:%20string) `target`> "-event" <[string](#Type:%20string) `eventName`> [... [string](#Type:%20string) `eventParam`]
* `Relay` <[string](#Type:%20string) `target`> ["-noredirect"] <... [string](#Type:%20string) `command`>


---
# Top-Level Objects
## TLO: Game

## TLO: Profile

## TLO: Mouse

## TLO: Keyboard

## TLO: Input

## TLO: Display

## TLO: Audio

## TLO: MIDI

## TLO: SettingXML

## TLO: Localization

## TLO: LavishSettings


---
# Types
## Type: dataset

### Members
- ??? `GUID[`???`]`
- ??? `Name[`???`]`
- ??? `Keys[`???`]`
- ??? `Key[`???`]`
- ??? `Set[`???`]`
- ??? `Sets[`???`]`
- ??? `GetString[`???`]`
- ??? `GetInt[`???`]`
- ??? `GetFloat[`???`]`

### Methods
- `SetName[`???`]`
- `Set[`???`]`
- `UnSet[`???`]`
- `Clear[`???`]`
- `AddSet[`???`]`
- `RemoveSet[`???`]`
- `Unload[`???`]`
- `Reload[`???`]`
- `Sort[`???`]`
- `Save[`???`]`



## Type: display

As Text: Same as `System`

### Members
- ??? `GetSize[`???`]`
- ??? `TaskbarAutoHide[`???`]`
- [string](#Type:%20string) `System`: Name of the current display system (e.g. Direct3D9)
- [bool](#Type:%20bool) `Windowed`: TRUE if the application is really windowed
- [bool](#Type:%20bool) `AppWindowed`: TRUE if the application thinks it is windowed
- [int](#Type:%20int) `Width`: The games actual resolution width
- [int](#Type:%20int) `Height`: The games actual resolution height
- [int](#Type:%20int) `X`: X position of the full windows left edge
- [int](#Type:%20int) `Y`: Y position of the full windows top edge
- [int](#Type:%20int) `WindowWidth`: Width of the full window
- [int](#Type:%20int) `WindowHeight`: Height of the full window
- [int](#Type:%20int) `Monitors`: Number of monitors
- [monitor](#Type:%20monitor) `Monitor`: Monitor assigned to the application
- [monitor](#Type:%20monitor) `Monitor[` `#` `]`: The #th monitor attached to the system (1-based)
- [int](#Type:%20int) `DesktopX`: X position of the left edge of the windows desktop on the current monitor
- [int](#Type:%20int) `DesktopY`: Y position of the top edge of the windows desktop on the current monitor
- [int](#Type:%20int) `DesktopWidth`: Width of the windows desktop on the current monitor
- [int](#Type:%20int) `DesktopHeight`: Height of the windows desktop on the current monitor
- [int](#Type:%20int) `ViewableX`: X position of the left edge of the windows viewable portion (does not include the border, etc)
- [int](#Type:%20int) `ViewableY`: Y position of the top edge of the windows viewable portion (does not include the border, etc)
- [int](#Type:%20int) `ViewableWidth`: Width of the windows viewable portion
- [int](#Type:%20int) `ViewableHeight`: Height of the windows viewable portion
- [bool](#Type:%20bool) `Foreground`: TRUE if the window is currently the active window on the system
- [int](#Type:%20int) `TextureMem`: Available texture memory, in megabytes
- [float](#Type:%20float) `FPS`: Sustained frames per second (calculated from the last 64 frames)
- [GDIWindow](#Type:%20GDIWindow) `Window`

### Methods
- `SetTaskbarAutoHide[`???`]`
- `Screencap[`???`]`
- `EnumWindows[`???`]`
- `EnumVisibleWindows[`???`]`



## Type: monitor

As Text: The monitor's 'name' according to Windows

### Members
- [int](#Type:%20int) `Width`: Width of the monitor in pixels
- [int](#Type:%20int) `Height`: Height of the monitor in pixels
- [int](#Type:%20int) `Left`: Left pixel of the monitor (X coordinate)
- [int](#Type:%20int) `Top`: Top pixel of the monitor (Y coordinate)
- [int](#Type:%20int) `Right`: Right pixel of the monitor (X coordinate)
- [int](#Type:%20int) `Bottom`: Bottom pixel of the monitor (Y coordinate)
- [int](#Type:%20int) `MaximizeWidth`: Width used for maximized windows on this monitor
- [int](#Type:%20int) `MaximizeHeight`: Height used for maximized windows on this monitor
- [int](#Type:%20int) `MaximizeLeft`: Left-most pixel used for maximized windows on this monitor
- [int](#Type:%20int) `MaximizeTop`: Top pixel used for maximized windows on this monitor
- [int](#Type:%20int) `MaximizeRight`: Right-most pixel used for maximized windows on this monitor
- [int](#Type:%20int) `MaximizeBottom`: Bottom pixel used for maximized windows on this monitor
- [bool](#Type:%20bool) `IsPrimary`: TRUE if the monitor is the Primary monitor
- ??? `ID[`???`]`
- [string](#Type:%20string) `Name`: Name of the monitor (e.g. \\.\DISPLAY1 -- you will need to use string.Escape to see the entire thing, or use string.Right[1] to get the monitor number for example)
- ??? `asJSON[`???`]`

### Methods
none.


## Type: audio

### Members
- [float](#Type:%20float) `VolumeLeft`: (Windows) Current Process left-channel volume level, as per Windows Volume Mixer. 0.0 for silent, 1.0 for full volume.
- [float](#Type:%20float) `VolumeRight`: (Windows) Current Process right-channel volume level, as per Windows Volume Mixer. 0.0 for silent, 1.0 for full volume.
- [float](#Type:%20float) `Volume`: (Windows) Current Process volume level, as per Windows Volume Mixer. 0.0 for silent, 1.0 for full volume.
- [bool](#Type:%20bool) `IsMuted`: (Windows) Current Process Mute setting, as per Windows Volume Mixer
- [audiovoice](#Type:%20audiovoice) `Voice[` `#` `]`: Retrieves an Audio Voice (something that makes sounds) by ID
- [jsonarray](#Type:%20jsonarray) `Voices`: Retrieves a JSON array containing the list of currently available Voices (things that make sounds)
- [audiostream](#Type:%20audiostream) `Stream[` `#` `]`: Retrieves an Audio Stream (a sound) by ID
- [jsonarray](#Type:%20jsonarray) `Streams`: Retrieves a JSON array containing the list of currently available Streams (sounds)
- [float](#Type:%20float) `EngineVolume`: The current Master volume level for Inner Spaces audio engine
- ??? `EngineVolumes[`???`]`

### Methods
- `FadeVolume[` `#` `,` `seconds` `]`: (Windows) Fades (adjusts) the Current Process volume level to the specified value, over the specified number of seconds.
- `SetVolume[` `#` `]`: (Windows) Sets the Current Process volume level to the specified value
- `SetVolume[` `#` `,` `#` `]`: (Windows) Sets the Current Process volume level to the specified left and right channel values
- `IncVolume[` `#` `]`: (Windows) Increases the Current Process volume level by the specified value
- `IncVolume[` `#` `,` `#` `]`: (Windows) Increases the Current Process volume level by the specified left and right channel values
- `SetMute[` `bool` `]`: (Windows) Sets the Current Process Mute setting
- `SetEngineVolume[` `#` `]`: Sets the Master volume level for Inner Spaces audio engine to the specified value
- `IncEngineVolume[` `#` `]`: Increments the Master volume level for Inner Spaces audio engine by the specified value
- `AddVoice[` `name` `]`: Creates a new Audio Voice (thing that makes sounds) with the specified name
- `RemoveVoice[` `name` `]`: Removes an Audio Voice with the specified name
- `AddStream[` `name` `,` `filename` `]`: Creates a new Audio Stream (a sound) with the specified name. The filename specifies the sound file to use for this stream.
- `RemoveStream[` `name` `]`: Removes an Audio Stream with the specified name



## Type: audiovoice

As Text: "audiovoice"

### Members
- ??? `Name[`???`]`
- ??? `ID[`???`]`
- ??? `NumChannels[`???`]`
- ??? `SampleRate[`???`]`
- ??? `Volume[`???`]`
- ??? `Volumes[`???`]`
- ??? `NowPlaying[`???`]`
- ??? `IsStarted[`???`]`
- ??? `IsPaused[`???`]`

### Methods
- `SetVolume[`???`]`
- `IncVolume[`???`]`
- `Start[`???`]`
- `Stop[`???`]`
- `Pause[`???`]`
- `ClearQueue[`???`]`
- `PlayStream[`???`]`
- `EnqueueStream[`???`]`



## Type: audiostream

As Text: "audiostream"

### Members
- ??? `Name[`???`]`
- ??? `ID[`???`]`
- ??? `NumChannels[`???`]`
- ??? `SampleRate[`???`]`
- ??? `Filename[`???`]`
- ??? `State[`???`]`

### Methods
- `BeginLoad[`???`]`
- `Unload[`???`]`



## Type: bind

As Text: "TRUE"

### Members
- [string](#Type:%20string) `Name`: The name of the bind
- [string](#Type:%20string) `Combo`: The key combination used for the bind
- [string](#Type:%20string) `PressCommand`: The command executed when this bind is pressed
- [string](#Type:%20string) `ReleaseCommand`: The command executed when this bind is released

### Methods
- `SetName[` `name` `]`: Renames the bind
- `SetCombo[` `combo` `]`: Changes the key combination used by the bind
- `SetPressCommand[` `command` `]`: Sets the command executed when this bind is pressed
- `SetReleaseCommand[` `command` `]`: Sets the command executed when this bind is released
- `Press[`???`]`
- `Release[`???`]`
- `Delete`: Deletes the bind



## Type: keyboard

### Members
- [string](#Type:%20string) `System`: Name of the currently active system for keyboard input (DirectInput, Win32I)

### Methods
- `Bind[` `name` `,` [key](#Type:%20key) `combination` `,` `command` `]`: Binds a command to a key combination, with a given name (see [[ISSession:Bind (Command)|Bind command]])
- `Bind[` `-press|-release` `,` `name` `,` [key](#Type:%20key) `combination` `,` `command` `]`: Binds a command to a key combination, with a given name (see [[ISSession:Bind (Command)|Bind command]])
- `GetButtonIterator[`???`]`
- `GetAxisIterator[`???`]`
- `GetDpadIterator[`???`]`
- `GetDeviceIterator[`???`]`
- `GetBindIterator[`???`]`
- `DisableBinds[`???`]`
- `EnableBinds[`???`]`



## Type: input

### Members
- ??? `G15[`???`]`
- ??? `Pending[`???`]`
- [button](#Type:%20button) `Button[` `name` `]`: Retrieves a button object by name
- [axis](#Type:%20axis) `Axis[` `name` `]`: Retrieves an axis object by name
- ??? `Device[`???`]`
- [dpad](#Type:%20dpad) `DPad[` `name` `]`: Retrieves a d-pad object by name
- [bind](#Type:%20bind) `Bind[` `name` `]`: Retrieves the bind with the given name
- [bool](#Type:%20bool) `BindsEnabled`

### Methods
none.


## Type: g15

As Text: "TRUE"

### Members
- [bool](#Type:%20bool) `M1Light`: TRUE if the M1 light is on
- [bool](#Type:%20bool) `M2Light`: TRUE if the M2 light is on
- [bool](#Type:%20bool) `M3Light`: TRUE if the M3 light is on
- [bool](#Type:%20bool) `MRLight`: TRUE if the MR light is on
- [uint](#Type:%20uint) `MLights`: Bit field with M-light states (M1=1,M2=2,M3=4,MR=8)
- [uint](#Type:%20uint) `BacklightLevel`: Keyboard backlight level (0 off, 1 medium, 2 high)
- [uint](#Type:%20uint) `LCDBacklightLevel`: LCD backlight level (0 off, 1 medium, 2 high)

### Methods
- `SetM1Light[` `value` `]`: TRUE for on, FALSE for off
- `SetM2Light[` `value` `]`: TRUE for on, FALSE for off
- `SetM3Light[` `value` `]`: TRUE for on, FALSE for off
- `SetMRLight[` `value` `]`: TRUE for on, FALSE for off
- `SetMLights[` `#` `]`: Set all 4 M-lights with a bit field (M1=1,M2=2,M3=4,MR=8)
- `SetBacklightLevel[` `#` `]`: Set keyboard backlight level (0 off, 1 medium, 2 high)
- `SetLCDBacklightLevel[` `#` `]`: Set LCD backlight level (0 off, 1 medium, 2 high)



## Type: button

### Members
- [string](#Type:%20string) `Name`: Name of the button
- [string](#Type:%20string) `Device`: Name of the input device hosting this button
- [uint](#Type:%20uint) `ID`: ID number of the button -- 255 and under are assigned by Windows, 256 and above are generated by Inner Space for non-keyboard buttons
- [bool](#Type:%20bool) `Pressed`: TRUE if this button is pressed

### Methods



## Type: axis

As Text: Same as `Name`

### Members
- [string](#Type:%20string) `Name`: Name of the axis
- [string](#Type:%20string) `Device`: Name of the input device hosting this axis
- [uint](#Type:%20uint) `ID`: ID number of the axis (independent of buttons or d-pads)
- [float](#Type:%20float) `Position`: Value between 0 and 1 indicating the axis position.  Generally 0 is to the left or downward, and 1 is to the right or upward.  Some axes are a bit more strange, such as Xbox 360 conroller triggers, where the value is the average position of the two triggers -- 0 is left trigger pulled, 1 is right trigger pulled, and 0.5 indicates both triggers are at rest, or both pulled.  The precision of this position is entirely based on the device and its driver (e.g. the values will not just be 0, 0.5, or 1, there might be thousands of possible values).

### Methods
none.


## Type: dpad

As Text: Same as `Name`

### Members
- [string](#Type:%20string) `Name`: Name of the d-pad
- [string](#Type:%20string) `Device`: Name of the input device hosting this d-pad
- [uint](#Type:%20uint) `ID`: ID number of the d-pad (independent of axes or buttons)
- [float](#Type:%20float) `Position`: Value between 0.00 and 360.00 clockwise, indicating the position as a direction.  A value of -1 indicates that the d-pad is at rest (in the middle)

### Methods
none.


## Type: inputdevice

### Members
- ??? `Name[`???`]`
- ??? `ID[`???`]`
- ??? `CurrentKeySet[`???`]`

### Methods
- `SelectKeySet[`???`]`



## Type: mouse

As Text: Same as `Position`

### Members
- [float](#Type:%20float) `Speed`: Current system mouse speed, 1.0 = 100%
- [int](#Type:%20int) `Threshold1`: Current system mouse acceleration threshold 1
- [int](#Type:%20int) `Threshold2`: Current system mouse acceleration threshold 2
- [int](#Type:%20int) `Acceleration`: Current system mouse acceleration setting
- ??? `DoubleClickTime[`???`]`
- ??? `DoubleClickWidth[`???`]`
- ??? `DoubleClickHeight[`???`]`
- [string](#Type:%20string) `System`: Name of the currently active system for mouse input (DirectInput, Win32I)
- [int](#Type:%20int) `X`: Current mouse X position (horizontal)
- [int](#Type:%20int) `Y`: Current mouse Y position (vertical)
- [string](#Type:%20string) `Position`: Position of the mouse, in the form X,Y, such as 0,0 or 263,475
- ??? `ConvertPosition[`???`]`
- ??? `TranslateX[`???`]`
- ??? `TranslateY[`???`]`
- ??? `ScaleX[`???`]`
- ??? `ScaleY[`???`]`
- [bool](#Type:%20bool) `Cursor`: TRUE if system cursor is visible

### Methods
- `ResetSpeed`: Resets system mouse speed to 100% (Speed=1.0) -- this will cause system lag when applied
- `DisableAcceleration`: Disables system mouse acceleration -- this will cause system lag when applied
- `ShowCursor`
- `HideCursor`



## Type: midi

As Text: "midi"

### Members
- ??? `NumAttachedInDevices[`???`]`
- ??? `AttachedInDevice[`???`]`
- ??? `AttachedInDevices[`???`]`
- [midiindevice](#Type:%20midiindevice) `InDevice[` `#` `]`: A MIDI In Device by its ID number (NOT the same number as Attached devices)
- ??? `NumInDevices[`???`]`
- [jsonarray](#Type:%20jsonarray) `InDevices`: A JSON array describing all open MIDI In devices
- ??? `NumAttachedOutDevices[`???`]`
- ??? `AttachedOutDevice[`???`]`
- ??? `AttachedOutDevices[`???`]`
- ??? `OutDevice[`???`]`
- ??? `NumOutDevices[`???`]`
- ??? `OutDevices[`???`]`

### Methods
- `OpenAllDevicesIn`: Opens all MIDI In devices, with controls mapped through [[LavishGUI 2]]. The port names will be generated as MIDI 1, MIDI 2, etc
- `CloseAllDevicesIn`: Closes all open MIDI In devices
- `OpenDeviceIn[` `#` `,` `portName` `]`: Opens the #th attached MIDI device (1-based), with controls mapped through [[LavishGUI 2]]. The specified portName is assigned to the device and can be used with the InDevice member
- `OpenDeviceIn[` `#` `,` `portName` `,` `object` `,` `method` `]`: Opens the #th attached MIDI device (1-based), with controls mapped through a [[LavishScript]] object method. The specified portName is assigned to the device and can be used with the InDevice member
- `OpenAllDevicesOut[`???`]`
- `CloseAllDevicesOut[`???`]`
- `OpenDeviceOut[`???`]`



## Type: midiindevice

As Text: "midiindevice"

### Members
- [jsonobject](#Type:%20jsonobject) `AsJSON`: A JSON summary of this device
- [jsonobject](#Type:%20jsonobject) `Metadata`: Metadata associated with this device
- [unistring](#Type:%20unistring) `Name`: The Port Name from this device, as passed to MIDI:OpenDeviceIn
- [unistring](#Type:%20unistring) `DeviceName`: The Name of the device itself, as specified by the device
- ??? `Retain[`???`]`

### Methods
- `Start`: Starts receiving MIDI input, to the receiver specified to MIDI:OpenDeviceIn (either [[LavishGUI 2]] or a LavishScript object method)
- `Stop`: Stops receiving MIDI input
- `Reset`: Resets MIDI input
- `Close`: Closes the midiindevice, which will then be removed from MIDI.InDevices and must be opened again via MIDI:OpenDeviceIn
- `SetRetain[`???`]`



## Type: midioutdevice

As Text: "midioutdevice"

### Members
- ??? `AsJSON[`???`]`
- ??? `Metadata[`???`]`
- ??? `Name[`???`]`
- ??? `DeviceName[`???`]`

### Methods
- `SendMessage[`???`]`
- `SendSysEx[`???`]`
- `SendNoteOn[`???`]`
- `SendNoteOff[`???`]`
- `SendNoteOnInt[`???`]`
- `SendNoteOffInt[`???`]`
- `SendProgram[`???`]`
- `SendControl[`???`]`
- `SendControlInt[`???`]`
- `SendPitchWheel[`???`]`
- `SendPolyphonicAftertouch[`???`]`
- `SendChannelAftertouch[`???`]`
- `SendPolyphonicAftertouchInt[`???`]`
- `SendChannelAftertouchInt[`???`]`
- `Close[`???`]`



## Type: midiinevent

As Text: "midiinevent"

### Members
- [emidimessage](#Type:%20emidimessage) `Message`: The Windows MIDI message: Open, Close, Data, LongData, Error, LongError
- [uint](#Type:%20uint) `Byte1`: Byte 1 of Data
- [uint](#Type:%20uint) `Byte2`: Byte 2 of Data
- [uint](#Type:%20uint) `Value`: This is a combination of Status, Byte1 and Byte2 (rather, they are derived from this value)
- [uint](#Type:%20uint) `Timestamp`: The MIDI timestamp from the event. This is the length of time since the midiindevice was Started or Reset
- [midiindevice](#Type:%20midiindevice) `Device`: The midiindevice that produced the event
- [uint](#Type:%20uint) `Status`: This is generally a combination of StatusCode and Channel (rather, they are derived from this value)
- [emidistatuscode](#Type:%20emidistatuscode) `StatusCode`: The MIDI Status Code: NoteOff, NoteOn, PolyphonicAftertouch, Control, Program, ChannelAftertouch, Pitch, System
- [uint](#Type:%20uint) `Channel`: For Channel-based Status Codes (all but System), this is the MIDI channel number

### Methods
none.


## Type: webrequest

As Text: "webrequest"

### Members
- [ewebrequeststate](#Type:%20ewebrequeststate) `State`: State of the webrequest, e.g. Idle, Queued, Working, Completed, Aborted
- [ewebrequestas](#Type:%20ewebrequestas) `InterpretAs`: How to interpret the servers response content, such as file, string, json or binary
- [string](#Type:%20string) `URL`: The URL to request
- [jsonarray](#Type:%20jsonarray) `POST`: A JSON array containing a list of objects that describe each POST parameter
- [string](#Type:%20string) `Filename`: The output filename, when interpreting as file
- [jsonobject](#Type:%20jsonobject) `Result`: A JSON object containing response codes and data received as a result of the request
- [binary](#Type:%20binary) `Binary`: A binary object containing the servers response content

### Methods
- `FromJSON[` `json` `]`: Initializes the webrequest via a JSON object. The webrequest must be in its Idle (Reset) state
- `Reset`: Resets the webrequest to its original Idle state, clearing any settings. The webrequest must not be in Working state. If in Queued state, this will act as :Abort instead
- `SetURL[` `url` `]`: Sets the URL to use. The webrequest must be in Idle or Queued state to change the URL.
- `InterpretAs[` `as` `]`: Tells the webrequest to provide the result as one of &lt;tt>string&lt;/tt>, &lt;tt>json&lt;/tt>, &lt;tt>binary&lt;/tt>
- `InterpretAs[` `file` `,` [absolute](#Type:%20absolute) `filename` `]`: Tells the webrequest to provide the result as a file, to the specified absolute filename (it is recommended to include the full path)
- `Begin`: Begins the webrequest. The webrequest must be in Idle state, and a URL must be set
- `Abort`: Aborts the webrequest. The webrequest must be in Queued state; an aborted webrequest will change to Aborted state when it otherwise would have changed to Working state.



## Type: agent

As Text: "agent"

### Members
- [uint](#Type:%20uint) `ID`: The Agents ID number, assigned when the Agent is loaded
- [unistring](#Type:%20unistring) `Name`: The Name of the Agent
- [bool](#Type:%20bool) `Started`: TRUE if the Agent is Started
- ??? `AutoStart[`???`]`
- [jsonobject](#Type:%20jsonobject) `Metadata`: Metadata associated with the Agent
- ??? `Args[`???`]`
- [filepath](#Type:%20filepath) `Directory`: If the Agent is in its own directory, this is that directory
- ??? `Version[`???`]`
- ??? `Description[`???`]`
- ??? `LGUI2MainElementName[`???`]`
- ??? `LGUI2MainElement[`???`]`
- ??? `MinimumBuild[`???`]`
- ??? `Provides[`???`]`
- ??? `Conflicts[`???`]`
- ??? `Dependencies[`???`]`

### Methods
- `Start`: Starts the Agent. Event handlers will start firing
- `Stop`: Stops the Agent. Event handlers will stop firing
- `Remove`: Stops and Removes the Agent
- `SetAutoStart[`???`]`
- `SetEventHandler[` `type` `,` `json` `]`: Where &lt;tt>type&lt;/tt> is one of "global" "platform" or "process", this sets a specified event handler to the given json
- `FireEvent[` `name` `]`: Fires the event by the specified name. Event handlers are processed in the following order: global, platform, process
- `FireEvent[` `-reverse` `,` `name` `]`: Fires the event by the specified name, in reverse order. This is used, for example, for "onAgentShutdown" to initiate the process shutdown, then platform shutdown, then global shutdown handlers



## Type: gdiwindow

### Initializers
- `gdiwindow[` [string](#Type:%20string) `hexHWND` `]`

As Text: hex HWND

### Members
- ??? `ProcessID[`???`]`
- ??? `ProcessName[`???`]`
- [???](#Type:%20???) `IsForeground`
- [???](#Type:%20???) `Monitor`
- [???](#Type:%20???) `HWND`
- ??? `IsMaximized[`???`]`
- ??? `IsVisible[`???`]`
- ??? `IsMouseOver[`???`]`
- [???](#Type:%20???) `Width`
- [???](#Type:%20???) `Height`
- [???](#Type:%20???) `X`
- [???](#Type:%20???) `Y`
- [???](#Type:%20???) `ViewableX`
- [???](#Type:%20???) `ViewableY`
- [???](#Type:%20???) `ViewableWidth`
- [???](#Type:%20???) `ViewableHeight`
- ??? `MenuWidth[`???`]`
- ??? `MenuHight[`???`]`
- ??? `Text[`???`]`
- [???](#Type:%20???) `AlwaysOnTop`
- [???](#Type:%20???) `Frame`
- ??? `Style[`???`]`

### Methods
- `Set[`???`]`
- `SetTaskbarTabVisible[`???`]`
- `Flash`: Causes window frame to flash
- `SetText`: Set window title



## Type: localization

As Text: Same as `Language`

### Members
- [string](#Type:%20string) `Language`: Name of the current language
- [string](#Type:%20string) `GetString[` `category` `,` `name` `]`: Retrieves a localized string with the given name, in the given category, if both exist
- [string](#Type:%20string) `GetString[` `category` `,` `name` `,` `default` `]`: Same as above, but will create the category and name if they do not exist, and the string will be populated with the default
- [bool](#Type:%20bool) `HasCategory[` `name` `]`: TRUE if a category with the given name exists in the current localization set

### Methods
- `SetString[` `category` `,` `name` `,` `value` `]`: Sets a localized string with the given name in the given category, creating both if necessary
- `RemoveString[` `category` `,` `name` `]`: Removes a localized string with the given name from the given category
- `RemoveCategory[` `category` `]`: Removes a given category (and any settings in it)
- `ExportLanguage[` [language](#Type:%20language) `name` `]`: Stores the current localization set (all categories and strings) as the given language (e.g. give a language name, not a filename)
- `ImportLanguage[` [language](#Type:%20language) `name` `]`: Imports a language into the current localization set, replacing any existing strings with those in the new language



## Type: lgui2videofeedsource
- Base Type: [lgui2element](#Type:%20lgui2element)

As Text: "lgui2videofeedsource"

### Members
- ??? `FeedName[`???`]`
- ??? `Feed[`???`]`

### Methods
- `SetFeedName[`???`]`



## Type: lgui2remotecontrol
- Base Type: [lgui2element](#Type:%20lgui2element)

As Text: "lgui2remotecontrol"

### Members

### Methods



## Type: lgui2videofeed
- Base Type: [lgui2remotecontrol](#Type:%20lgui2remotecontrol)

As Text: "lgui2videofeed"

### Members
- ??? `FeedName[`???`]`
- ??? `Feed[`???`]`
- ??? `Permanent[`???`]`

### Methods
- `SetFeedName[`???`]`
- `SetPermanent[`???`]`



## Type: lgui2broadcaster
- Base Type: [lgui2remoteonctrol](#Type:%20lgui2remoteonctrol)

As Text: "lgui2broadcaster"

### Members

### Methods



## Type: lavishsettings
- Base Type: [settingset](#Type:%20settingset)

As Text: Same as `Name`

### Members
- ??? `Version[`???`]`
- ??? `Tree[`???`]`
- ??? `SetByID[`???`]`

### Methods
none.


## Type: settingnode

### Members
- ??? `Parent[`???`]`
- ??? `Next[`???`]`
- ??? `Previous[`???`]`

### Methods
- `Remove[`???`]`



## Type: setting
- Base Type: [settingnode](#Type:%20settingnode)

As Text: Same as `String`

### Members
- ??? `Name[`???`]`
- ??? `String[`???`]`
- ??? `Int[`???`]`
- ??? `Float[`???`]`
- ??? `FindAttribute[`???`]`
- ??? `AsJSON[`???`]`

### Methods
- `Rename[`???`]`
- `Set[`???`]`
- `AddAttribute[`???`]`



## Type: settingattribute
- Base Type: [settingnode](#Type:%20settingnode)

As Text: Same as `String`

### Members
- ??? `Name[`???`]`
- ??? `String[`???`]`
- ??? `Int[`???`]`
- ??? `Float[`???`]`

### Methods
- `Rename[`???`]`
- `Set[`???`]`



## Type: settingset
- Base Type: [settingnode](#Type:%20settingnode)

### Indexers
- [string](#Type:%20string) `settingset`

As Text: Same as `GUID`

### Members
- ??? `Children[`???`]`
- ??? `AsJSON[`???`]`
- ??? `Name[`???`]`
- ??? `GUID[`???`]`
- ??? `Get[`???`]`
- ??? `FindSet[`???`]`
- ??? `FindSetting[`???`]`
- ??? `FindAttribute[`???`]`

### Methods
- `Import[`???`]`
- `Reload[`???`]`
- `ImportJSON[`???`]`
- `Export[`???`]`
- `ExportJSON[`???`]`
- `AddSet[`???`]`
- `AddComment[`???`]`
- `AddSetting[`???`]`
- `AddAttribute[`???`]`
- `Rename[`???`]`
- `Clear[`???`]`
- `Sort[`???`]`
- `Copy[`???`]`
- `GetIterator[`???`]`
- `GetSetIterator[`???`]`
- `GetSettingIterator[`???`]`
- `GetCommentIterator[`???`]`



## Type: settingcomment
- Base Type: [settingnode](#Type:%20settingnode)

As Text: Same as `Text`

### Members
- ??? `Text[`???`]`

### Methods
- `Set[`???`]`



## Type: settingsetref
- Base Type: [settingset](#Type:%20settingset)

### Initializers
`settingsetref`
- `settingsetref[` [uint](#Type:%20uint) `]`

### Members
- ??? `GUID[`???`]`

### Methods
- `Set[`???`]`



Joe Multiboxer Kernel API Specification (LavishScript)

---
# Events
## Event: JMB_OnSlotUpdated

## Event: JMB_OnCharacterChanged

## Event: JMB_OnCharacterUpdated

## Event: JMB_OnCharactersUpdated

## Event: JMB_OnSlotsUpdated

## Event: JMB_OnTeamsUpdated

## Event: JMB_OnTeamUpdated

## Event: JMB_OnTeamChanged

## Event: JMB_OnMasterSlotChanged


---
# Commands
none.

---
# Top-Level Objects
## TLO: JMB
- [joemultiboxer](#Type:%20joemultiboxer) `JMB`


---
# Types
## Type: joemultiboxer

### Members
- [string](#Type:%20string) `Version`
- [int](#Type:%20int) `Build`
- [string](#Type:%20string) `Uplink`
- [jmbslot](#Type:%20jmbslot) `Slot`
- [jmbslot](#Type:%20jmbslot) `Slot[` [uint](#Type:%20uint) `numSlot` `]`
- [jsonarray](#Type:%20jsonarray) `Slots`
- [lgui2team](#Type:%20lgui2team) `Team`
- [lgui2team](#Type:%20lgui2team) `Team[` [uint](#Type:%20uint) `id` `]`
- [lgui2team](#Type:%20lgui2team) `Team[` [string](#Type:%20string) `search` `]`
- [jsonarray](#Type:%20jsonarray) `Teams`
- [lgui2character](#Type:%20lgui2character) `Character`
- [lgui2character](#Type:%20lgui2character) `Character[` [uint](#Type:%20uint) `id` `]`
- [lgui2character](#Type:%20lgui2character) `Character[` [string](#Type:%20string) `search` `]`
- [jsonarray](#Type:%20jsonarray) `Characters`
- [uint](#Type:%20uint) `Agent`
- [string](#Type:%20string) `Agent`
- [jsonarray](#Type:%20jsonarray) `Agents`
- [jmbslot](#Type:%20jmbslot) `ForegroundSlot`
- [jmbslot](#Type:%20jmbslot) `MouseOverSlot`
- [jmbslot](#Type:%20jmbslot) `MasterSlot`
- [jmbteam](#Type:%20jmbteam) `AddTeam[` [jsonobject](#Type:%20jsonobject) `json` `]`
- [jmbslot](#Type:%20jmbslot) `AddSlot`
- [jmbcharacter](#Type:%20jmbcharacter) `AddCharacter[` [jsonobject](#Type:%20jsonobject) `json` `]`
- [settingsetref](#Type:%20settingsetref) `GameConfiguration`
- [settingsetref](#Type:%20settingsetref) `InputConfiguration`

### Methods
- `AddCharacter[` [jsonobject](#Type:%20jsonobject) `json` `]`
- `AddTeam[` [jsonobject](#Type:%20jsonobject) `json` `]`
- `AddSlot`
- `ClearSlots`
- `LoadJMBSettings`
- `LoadJMBSettings[` [string](#Type:%20string) `filename` `]`
- `StoreJMBSettings`
- `StoreJMBSettings[` [string](#Type:%20string) `filename` `]`
- `SetMasterSlot[` [uint](#Type:%20uint) `numSlot` `]`
- `ScanAgentsFolder`
- `AddAgent[` [jsonobject](#Type:%20jsonobject) `json` `]`
- `FireAgentEvent[` <"-reverse"> `,` [string](#Type:%20string) `name` `,` [jsonobject](#Type:%20jsonobject) `eventArgs` `]`
- `AddTeamSlots[` [uint](#Type:%20uint) `teamID` `]`
- `RemoveTeamSlots[` [uint](#Type:%20uint) `teamID` `]`
- `RemoveUnusedSlots[`???`]`



## Type: jmbcharacter

As Text: Same as `ID`

### Members
- [jsonobject](#Type:%20jsonobject) `AsJSON`
- [int64](#Type:%20int64) `ID`
- [unistring](#Type:%20unistring) `DisplayName`
- [unistring](#Type:%20unistring) `ActualName`
- [unistring](#Type:%20unistring) `Server`
- [unistring](#Type:%20unistring) `Game`
- [unistring](#Type:%20unistring) `GameProfile`
- [jsonobject](#Type:%20jsonobject) `Metadata`
- [jmbvirtualfile](#Type:%20jmbvirtualfile) `VirtualFile[` [string](#Type:%20string) `pattern` `]`
- [jsonarray](#Type:%20jsonarray) `VirtualFiles`

### Methods
- `Remove`
- `SetDisplayName[` [string](#Type:%20string) `newValue` `]`
- `SetActualName[` [string](#Type:%20string) `newValue` `]`
- `SetServer[` [string](#Type:%20string) `newValue` `]`
- `SetGame[` [string](#Type:%20string) `newValue` `]`
- `SetGameProfile[` [string](#Type:%20string) `newValue` `]`
- `AddVirtualFile[` <"-exact"> `,` [string](#Type:%20string) `pattern` `,` [string](#Type:%20string) `replacement` `,` <[string](#Type:%20string) `target`="all"> `]`
- `RemoveVirtualFile[` [string](#Type:%20string) `pattern` `]`
- `ClearVirtualFiles`



## Type: jmbteam

As Text: Same as `ID`

### Members
- [jsonobject](#Type:%20jsonobject) `AsJSON`
- [int64](#Type:%20int64) `ID`
- [unistring](#Type:%20unistring) `DisplayName`
- [jsonobject](#Type:%20jsonobject) `Metadata`
- [jmbvirtualfile](#Type:%20jmbvirtualfile) `VirtualFile[` [string](#Type:%20string) `pattern` `]`
- [jsonarray](#Type:%20jsonarray) `VirtualFiles`
- [int64](#Type:%20int64) `Slot[` [uint](#Type:%20uint) `numSlot` `]`: Retrieves the Character ID for a given Slot number
- [jsonarray](#Type:%20jsonarray) `Slots`
- [jmbcharacter](#Type:%20jmbcharacter) `Character[` [uint](#Type:%20uint) `numSlot` `]`: Retrieves the Character for a given Slot number
- [jsonarray](#Type:%20jsonarray) `Characters`
- [uint](#Type:%20uint) `AddCharacter[` [int64](#Type:%20int64) `characterID` `]`: Adds a Character to the Team, returning its new Slot number
- [uint](#Type:%20uint) `MasterSlot`
- [uint](#Type:%20uint) `DefaultMasterSlot`

### Methods
- `SetDefaultMasterSlot[` [uint](#Type:%20uint) `numSlot` `]`
- `Remove`
- `SetDisplayName[` [string](#Type:%20string) `newValue` `]`
- `AddVirtualFile[` <"-exact"> `,` [string](#Type:%20string) `pattern` `,` [string](#Type:%20string) `replacement` `,` <[string](#Type:%20string) `target`="all"> `]`
- `RemoveVirtualFile[` [string](#Type:%20string) `pattern` `]`
- `ClearVirtualFiles`
- `ClearSlots`
- `AddCharacter[` [int64](#Type:%20int64) `characterID` `]`
- `RemoveCharacter[` [int64](#Type:%20int64) `characterID` `]`
- `RemoveSlot[` [uint](#Type:%20uint) `numSlot` `]`



## Type: jmbslot

As Text: Same as `ID`

### Members
- [jsonobject](#Type:%20jsonobject) `AsJSON`: JSON representation of the Slot
- [uint](#Type:%20uint) `ID`
- [uint](#Type:%20uint) `ProcessID`
- [jmbcharacter](#Type:%20jmbcharacter) `Character`: The Character, if any, assigned to the Slot
- [jmbteam](#Type:%20jmbteam) `Team`: The Team, if any, assigned to the Slot
- [uint](#Type:%20uint) `TeamSlot`: The Team Slot (number within the Team) assigned to this Slot
- [bool](#Type:%20bool) `IsMasterSlot`: TRUE if the Slot is currently assigned Team's Master Slot

### Methods
- `Launch`: Launches the Slot, if not already running
- `Close`: Requests the Slot close gracefully, possibly allowing the process to save data, etc
- `Remove`: Removes the Slot
- `SetCharacter[` [uint](#Type:%20uint) `characterID` `]`
- `SetCharacter[` [string](#Type:%20string) `characterName` `]`
- `SetMasterSlot`



## Type: jmbvirtualfile

As Text: "virtualfile"

### Members
- [jsonobject](#Type:%20jsonobject) `AsJSON`
- [string](#Type:%20string) `Pattern`
- [string](#Type:%20string) `Replacement`
- [bool](#Type:%20bool) `ExactMatch`
- [bool](#Type:%20bool) `IsStarted`
- [string](#Type:%20string) `Target`

### Methods
- `SetPattern[` [string](#Type:%20string) `pattern` `,` [bool](#Type:%20bool) `exactMatch`=false `]`
- `SetReplacement[` [string](#Type:%20string) `replacement` `]`
- `SetTarget[` [string](#Type:%20string) `target` `]`
- `Start`
- `Stop`



Inner Space Uplink API Specification (LavishScript)

---
# Events
## Event: GamesChanged

## Event: OnSessionConnected

## Event: OnSessionRenamed

## Event: OnSessionDisconnected


---
# Commands
## Command: MainWindow
### Syntax
* `MainWindow` "-show"|"-hide"|"-toggle"

## Command: WindowSize
### Syntax
* `WindowSize`
* `WindowSize` ["-rescale"] "-fullscreen"|"-reset"
* `WindowSize` ["-rescale"] ["-viewable"] <[string](#Type:%20string) `widthAndHeight`>

## Command: Speak
### Syntax
* `Speak` ["-async"] ["-volume" <[float](#Type:%20float) `newVolume`>] ["-speed" <[float](#Type:%20float) `newSpeed`>] <[string](#Type:%20string) `text`>

## Command: RestoreGamma
### Syntax
* `RestoreGamma`

## Command: RelayGroup
### Syntax
* `RelayGroup` "-list"|"-clear"
* `RelayGroup` "-join"|"-leave" <[string](#Type:%20string) `name`>

## Command: Name
### Syntax
* `Name` <[string](#Type:%20string) `name`>
  * Sets the Name of the current Session (must be sent from a local Session)

## Command: RelayTargets
### Syntax
* `RelayTargets` <[string](#Type:%20string) `relayTarget`>

## Command: Sessions
### Syntax
* `Sessions`

## Command: Kill
### Syntax
* `Kill` <[string](#Type:%20string) `sessionName`>

## Command: Attach
### Syntax
* `Attach` <[uint](#Type:%20uint) `pid`> <[string](#Type:%20string) `gameName`> <[string](#Type:%20string) `gameProfileName`> [... `startupOptions` ["-loader" "none"|"minimum"|"moderate"|"standard"|"maximum"|"-startup" <[string](#Type:%20string) `command`>|"-prestartup" <[string](#Type:%20string) `command`>|"-character" <[int64](#Type:%20int64) `characterID`>]]

## Command: Open
### Syntax
* `Open` <[string](#Type:%20string) `gameName`> <[string](#Type:%20string) `gameProfileName`> [... `startupOptions` ["-loader" "none"|"minimum"|"moderate"|"standard"|"maximum"|"-nogameprofileparams"|"-addparam" <[string](#Type:%20string) `value`>|"-startup" <[string](#Type:%20string) `command`>|"-prestartup" <[string](#Type:%20string) `command`>|"-character" <[int64](#Type:%20int64) `characterID`>]]

## Command: Focus
### Syntax
* `Focus` <[string](#Type:%20string) `sessionName`>
* `Focus` "-next"|"-previous"|"-first"|"-last" [[string](#Type:%20string) `filter`]

## Command: MakeShortcut
### Syntax
* `MakeShortcut` <[string](#Type:%20string) `gameName`> <[string](#Type:%20string) `gameProfileName`>


---
# Top-Level Objects
## TLO: LicenseServer
- [licenseserver](#Type:%20licenseserver) `LicenseServer`

## TLO: Sessions

## TLO: Session

## TLO: ISMenu

## TLO: VideoFeed
- [videofeed](#Type:%20videofeed) `VideoFeed`

## TLO: Speech
- [speech](#Type:%20speech) `Speech`


---
# Types
## Type: licenseserver

### Members
- [uint](#Type:%20uint) `CheckPatchTime`
- [string](#Type:%20string) `ExpirationDate`
- [int](#Type:%20int) `PatchFiles`
- [jsonobject](#Type:%20jsonobject) `LiveBuild`
- [jsonobject](#Type:%20jsonobject) `DevBuild`
- [bool](#Type:%20bool) `UseDevBuild`

### Methods
- `CheckPatch[`???`]`
- `ApplyPatch[` [string](#Type:%20string) `branch` `,` [string](#Type:%20string) `version` `]`



## Type: session

As Text: Same as `Name`

### Members
- [string](#Type:%20string) `Name`
- [bool](#Type:%20bool) `IsLocal`
- [uint](#Type:%20uint) `PID`
- [gdiwindow](#Type:%20gdiwindow) `Window`
- [string](#Type:%20string) `Executable`

### Methods
- `Execute[` <"-noredirect"> `,` [string](#Type:%20string) `command` `]`
- `Kill`



## Type: speech

### Members
- ??? `Ready[`???`]`

### Methods
- `Speak[`???`]`
- `Initialize[`???`]`
- `Stop[`???`]`
- `DumpVoices[`???`]`



## Type: ismenuitem

As Text: Same as `ID`

### Members
- ??? `Type[`???`]`
- ??? `Name[`???`]`
- ??? `ID[`???`]`
- ??? `Parent[`???`]`
- ??? `Next[`???`]`
- ??? `Previous[`???`]`
- ??? `IsChecked[`???`]`

### Methods
- `SetCheck[`???`]`
- `Remove[`???`]`
- `Rename[`???`]`



## Type: ismenu


### Members
- ??? `AddCommand[`???`]`
- ??? `AddSeparator[`???`]`
- ??? `AddSubMenu[`???`]`
- ??? `Children[`???`]`
- ??? `FindChild[`???`]`
- ??? `ChildCount[`???`]`

### Methods
- `Clear[`???`]`
- `AddCommand[`???`]`
- `AddSeparator[`???`]`
- `AddSubMenu[`???`]`



## Type: ismenucommand

### Members
- ??? `Command[`???`]`

### Methods
- `SetCommand[`???`]`
- `Execute[`???`]`



## Type: ismenuseparator

### Members
none.
### Methods
none.


## Type: videofeed

### Members
none.
### Methods
- `RegisterSource[`???`]`
- `RegisterOutput[`???`]`
- `UnregisterSource[`???`]`
- `UnregisterOutput[`???`]`
- `DumpSources[`???`]`
- `DumpOutputs[`???`]`



