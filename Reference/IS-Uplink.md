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
* `DeclareVariable` < [<[string](#type-string) `varName`>|<[string](#type-string) `varName[... uint arrayExtents]`>]> [[string](#type-string) `typeName`="string"] "globalkeep"|"global"|"script"|"object"|"local" <[string](#type-string) `initialValue`>

## Command: DeleteVariable
### Syntax
* `DeleteVariable` <[string](#type-string) `varName`>

## Command: RunScript
### Syntax
* `RunScript` <[string](#type-string) `filename`> [... [string](#type-string) `scriptParams`]

## Command: EndScript
### Syntax
* `EndScript` <[string](#type-string) `filename`>
* `EndScript` "*"

## Command: Execute

## Command: OSExecute
- Restricted: Yes


## Command: Return
### Syntax
* `Return` [... [string](#type-string) `returnObjectInitParams`]

## Command: Call
### Syntax
* `Call` <[string](#type-string) `functionName`> [... [string](#type-string) `functionParams`]

## Command: Wait
### Syntax
* `Wait` < [<[uint](#type-uint) `deciseconds`>|"-s" <[float](#type-float) `seconds`>]> [[bool](#type-bool) `pauseUntilExpression`]

## Command: WaitScript
### Syntax
* `WaitScript` <[string](#type-string) `filename`> <... [string](#type-string) `scriptParams`>

## Command: ExecuteFile
- Restricted: Yes


## Command: Cat
- Restricted: Yes


## Command: Head
- Restricted: Yes


## Command: Tail
- Restricted: Yes


## Command: Line
- Restricted: Yes


## Command: cd
- Restricted: Yes


## Command: mkdir
- Restricted: Yes

### Syntax
* `mkdir` <[string](#type-string) `path`>

## Command: rmdir
- Restricted: Yes


## Command: rename
- Restricted: Yes


## Command: rm
- Restricted: Yes


## Command: cp
- Restricted: Yes


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
* `LSType` <[string](#type-string)>

## Command: TopLevelObject
### Syntax
* `TopLevelObject`

## Command: TimedCommand

## Command: QueueCommand
### Syntax
* `QueueCommand` <... [string](#type-string) `command`>

## Command: ExecuteQueued
### Syntax
* `ExecuteQueued` [[string](#type-string) `needle`]

## Command: FlushQueued
### Syntax
* `FlushQueued` [[string](#type-string) `needle`]

## Command: NoOp

## Command: Turbo
### Syntax
* `Turbo` [[uint](#type-uint) `maxCommandsPerPulse`=150]

## Command: Module
- Restricted: Yes


## Command: APICall
- Restricted: Yes


## Command: Processor

## Command: ExecuteAtom

## Command: AddAtom

## Command: DeleteAtom

## Command: Squelch
### Syntax
* `Squelch` <... [string](#type-string) `command`>

## Command: Echo
### Syntax
* `Echo` <... [string](#type-string) `text`>

## Command: AddTrigger
### Syntax
* `AddTrigger` <[string](#type-string) `functionName`> <[string](#type-string) `needle`>

## Command: RemoveTrigger
### Syntax
* `RemoveTrigger` <[string](#type-string) `functionName`>

## Command: WaitFor
### Syntax
* `WaitFor` <... [string](#type-string) `upTo20needles`> [[uint](#type-uint) `maxWaitDeciseconds`]


---
# Top-Level Objects
## TLO: Type
- [type](#type-type) `Type[` [string](#type-string) `typeName` `]`

## TLO: Int
- [int](#type-int) `Int[` [int](#type-int) `value` `]`

## TLO: Int64
- [int64](#type-int64) `Int64[` [int64](#type-int64) `value` `]`

## TLO: String
- [string](#type-string) `String[` [string](#type-string) `value` `]`

## TLO: Float
- [int](#type-int) `Float[` [int](#type-int) `value` `]`

## TLO: Bool
- [bool](#type-bool) `Bool[` [bool](#type-bool) `value` `]`

## TLO: If
- [string](#type-string) `If[` [float64](#type-float64) `condition` `,` [string](#type-string) `trueValue` `,` <[string](#type-string) `falseValue`=""> `]`: If `condition` is non-zero, results in `trueValue`, otherwise `falseValue`

## TLO: Time
- [time](#type-time) `Time`: The current local date/time

## TLO: Enum
- [enumtype](#type-enumtype) `Enum[` [string](#type-string) `enumName` `]`

## TLO: ForEach
- [keyvaluepair](#type-keyvaluepair) `ForEach`: Current Key,Value in a currently-executing ForEach

## TLO: Return
- [object](#type-object) `Return`: The returned value from the last Call, from the current script

## TLO: Returning
- [object](#type-object) `Returning`: The instantiated object to be returned from the current function/member

## TLO: Variable
- [object](#type-object) `Variable[` [string](#type-string) `descriptor` `]`

## TLO: QueuedCommands
- [bool](#type-bool) `QueuedCommands`: TRUE if commands are currently queued for the current script
- [bool](#type-bool) `QueuedCommands[` [string](#type-string) `commandSubstring` `]`: TRUE if commands containing the `commandSubstring` are currently queued for the current script

## TLO: Arg
- [string](#type-string) `Arg[` [uint](#type-uint) `numArg` `,` ... [string](#type-string) `args` `]`

## TLO: Script
- [script](#type-script) `Script`: Currently executing script, if any
- [script](#type-script) `Script[` [string](#type-string) `scriptFile` `]`

## TLO: Function
- [function](#type-function) `Function`: Currently executing function, from the current Script, if any

## TLO: Execute
- [int](#type-int) `Execute[` [string](#type-string) `command` `]`

## TLO: Select
- [int](#type-int) `Select[` [string](#type-string) `needle` `,` ... [string](#type-string) `haystack` `]`: Finds the index of a value within `haystack` matching `needle`
- [object](#type-object) `Select`: The object currently being tested within a LavishScript Select query (not to be confused with the other form of this TLO)

## TLO: This
- [weakref](#type-weakref) `This`
- [weakref](#type-weakref) `This[` "parent" `]`

## TLO: Event
- [event](#type-event) `Event[` [uint](#type-uint) `eventID` `]`
- [event](#type-event) `Event[` [string](#type-string) `eventName` `]`

## TLO: WaitFor
- [int](#type-int) `WaitFor`: The last WaitFor result, from the currently executing script

## TLO: VariableScope
- [variablescope](#type-variablescope) `VariableScope`: The current local Variable Scope for the currently executing script if there is one, otherwise the global Variable Scope

## TLO: PersistentObject
- [weakref](#type-weakref) `PersistentObject[` [uint](#type-uint) `handle` `]`

## TLO: Query
- [bool](#type-bool) `Query[` [object](#type-object) `obj` `,` [string](#type-string) `expression` `]`

## TLO: LMAC
- [lavishmachine](#type-lavishmachine) `LMAC`

## TLO: Math
- [math](#type-math) `Math`

## TLO: System
- [system](#type-system) `System`

## TLO: LavishScript
- [lavishscript](#type-lavishscript) `LavishScript`


---
# Enums
none.

---
# Types
## Type: int
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `int[` <[int](#type-int) `value`=0> `]`


### Members
- [int](#type-int) `Inc[` <[int](#type-int) `expression`=1> `]`: Returns this int, plus a given amount
- [int](#type-int) `Dec[` <[int](#type-int) `expression`=1> `]`: Returns this int, minus a given amount
- [int](#type-int) `Mul[` [int](#type-int) `expression` `]`: Returns this int, multiplied by a given amount
- [int](#type-int) `Div[` [int](#type-int) `expression` `]`: Returns this int, multiplied by a given amount
- [float](#type-float) `Float`: This number, converted to a float
- [string](#type-string) `Hex`: A hexadecimal string equivalent to this number
- [string](#type-string) `LeadingZeroes[` [uint](#type-uint) `digits` `]`: A string representation of this number, with at least this many decimal places.  The number will be lead with zeroes to reach the desired length
- [int](#type-int) `Reverse`: This number, with its bytes reversed (1234 is turned into 3523477504.. easier to see in hex: 00 00 04 D2 -> D2 04 00 00)
- [bool](#type-bool) `Between[` [int](#type-int) `,` [int](#type-int) `]`: TRUE if   a<= value and value <= b
- [uint](#type-uint) `Unsigned`: This number as 32-bit unsigned
- [bool](#type-bool) `Equal[` [int](#type-int) `expression` `]`: TRUE if the int matches the specified value
- [string](#type-string) `AsJSON`: A string with the value of the int, as would be in JSON

### Methods
- `Reverse`
- `Inc[` <[int](#type-int) `expression`=1> `]`: Increments this int by a given amount
- `Inc`: Increments this int by 1
- `Dec[` <[int](#type-int) `expression`=1> `]`: Decrements this int by a given amount
- `Dec`: Decrements this int by 1
- `Mul[` [int](#type-int) `expression` `]`: Multiplies this int by a given amount
- `Div[` [int](#type-int) `expression` `]`: Divides this int by a given amount
- `Set[` [int](#type-int) `expression` `]`: Sets this int to a given value

### Static Members
- [int](#type-int) `Min`
- [int](#type-int) `Max`



## Type: uint
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `uint[` <[uint](#type-uint) `value`=0> `]`


### Members
- [uint](#type-uint) `Inc[` <[uint](#type-uint) `expression`=1> `]`: Returns this uint, plus a given amount
- [uint](#type-uint) `Dec[` <[uint](#type-uint) `expression`=1> `]`: Returns this uint, minus a given amount
- [uint](#type-uint) `Mul[` [uint](#type-uint) `expression` `]`: Returns this uint, multiplied by a given amount
- [uint](#type-uint) `Div[` [uint](#type-uint) `expression` `]`: Returns this uint, multiplied by a given amount
- [float](#type-float) `Float`: This number, converted to a float
- [string](#type-string) `Hex`: A hexadecimal string equivalent to this number
- [string](#type-string) `LeadingZeroes[` `#` `]`: A string representation of this number, with at least this many decimal places.  The number will be lead with zeroes to reach the desired length
- [uint](#type-uint) `Reverse`: This number, with its bytes reversed (1234 is turned into 3523477504.. easier to see in hex: 00 00 04 D2 -> D2 04 00 00)
- [bool](#type-bool) `Between[` [int](#type-int) `,` [int](#type-int) `]`: TRUE if   a<= value and value <= b
- [int](#type-int) `Signed`: This number as 32-bit signed
- [bool](#type-bool) `Equal[` [formula](#type-formula) `]`: TRUE if the uint matches the specified value
- [string](#type-string) `AsJSON`: A string with the value of the uint, as would be in JSON

### Methods
- `Reverse[`???`]`
- `Inc[` <[uint](#type-uint) `expression`=1> `]`: Increments this uint by a given amount
- `Inc`: Increments this uint by 1
- `Dec[` <[uint](#type-uint) `expression`=1> `]`: Decrements this uint by a given amount
- `Dec`: Decrements this uint by 1
- `Mul[` [uint](#type-uint) `expression` `]`: Multiplies this uint by a given amount
- `Div[` [uint](#type-uint) `expression` `]`: Divides this uint by a given amount
- `Set[` [formula](#type-formula) `]`: Sets this uint to a given value

### Static Members
- [uint](#type-uint) `Min`
- [uint](#type-uint) `Max`



## Type: string
- Persistent: No ([weakref](#type-weakref) not supported)

### Indexers
- [byte](#type-byte) `string[` [uint](#type-uint) `position` `]`

### Members
- [string](#type-string) `Mid[` [uint](#type-uint) `position` `,` [uint](#type-uint) `length` `]`: Returns a string containing the given length at the given position (1-based) of the original string
- [string](#type-string) `Left[` [int](#type-int) `length` `]`: Returns a string containing the leftmost # characters of the original string. A negative number can be used to give the leftmost (Length-#)
- [string](#type-string) `Right[` [int](#type-int) `length` `]`: Returns a string containing the rightmost # characters of the original string. A negative number can be used to give the rightmost (Length-#)
- [int64](#type-int64) `Find[` [string](#type-string) `needle` `]`: Returns the 1-based position of a given substring in the original string, or NULL
- [int64](#type-int64) `Find[` ... [string](#type-string) `possible_needles` `]`: Returns the 1-based position of the first of several substrings to be found in the original string, or NULL
- [jsonobject](#type-jsonobject) `FindAnyOf[` ... [string](#type-string) `possible_needles` `]`: Returns the 1-based position, and what was found, of the first of several substrings to be found in the original string, or NULL
- [jsonobject](#type-jsonobject) `FindAnyOfArray[` [jsonvalueref](#type-jsonvalueref) `arrayOfStrings` `]`: Returns the 1-based position, and what was found, of the first of several substrings to be found in the original string, or NULL
- [int64](#type-int64) `FindFrom[` [uint](#type-uint) `position` `,` [string](#type-string) `needle` `]`
- [int64](#type-int64) `Length`: Returns the length of the string
- [string](#type-string) `Upper`: Returns a string containing the original string in all upper case
- [string](#type-string) `Lower`: Returns a string containing the original string in all lower case
- [int](#type-int) `Compare[` [string](#type-string) `compareTo` `]`: Compares this string, without regards to case, to the given text. Return value is less than 0 if the text would come before it in the dictionary, 0 if it is equal, or greater than 0 if the text would come after the string
- [int](#type-int) `CompareCS[` [string](#type-string) `compareTo` `]`: Compares this string, with regards to case, to the given text. Return value is less than 0 if the text would come before it in the dictionary, 0 if it is equal, or greater than 0 if the text would come after the string
- [bool](#type-bool) `Equal[` [string](#type-string) `compareTo` `]`: TRUE if the string is equal to, without regards to case, the given text
- [bool](#type-bool) `NotEqual[` [string](#type-string) `compareTo` `]`: TRUE if the string is not equal to, without regards to case, the given text
- [bool](#type-bool) `EqualCS[` [string](#type-string) `compareTo` `]`: TRUE if the string is equal to, with regards to case, the given text
- [bool](#type-bool) `NotEqualCS[` [string](#type-string) `compareTo` `]`: TRUE if the string is not equal to, with regards to case, the given text
- [bool](#type-bool) `Equals[` [string](#type-string) `compareTo` `]`
- [bool](#type-bool) `NotEquals[` [string](#type-string) `compareTo` `]`
- [bool](#type-bool) `EqualsCS[` [string](#type-string) `compareTo` `]`
- [bool](#type-bool) `NotEqualsCS[` [string](#type-string) `compareTo` `]`
- [int](#type-int) `Count[` [string](#type-string) `findCharacter` `]`: The number of times a specific character appears in the string
- [string](#type-string) `Token[` [string](#type-string) `token` `,` [uint](#type-uint) `numToken` `]`: "Tokenizes" the string by the given separator and returns the #th token
- [string](#type-string) `EscapeQuotes`: Uses slashes to escape " only
- [string](#type-string) `Escape[` <[uint](#type-uint) `mode`=1> `]`: If escapeLavishScript is false/0, Uses slashes to escape \, ", carriage return, line feed, tab, but NOT LavishScript data sequences
- [string](#type-string) `Escape`: Uses slashes to escape \, ", carriage return, line feed, tab, as well as LavishScript data sequences
- [string](#type-string) `Replace[` `character` `,` `with` `,` ... [string](#type-string) `]`: Performs single-character replacement with any number of character pairs
- [byte](#type-byte) `GetAt[` [uint](#type-uint) `position` `]`: Retrieves a character at the #th position in the string (1-based)
- [unistring](#type-unistring) `UniString`
- [string](#type-string) `URLEncode`: Returns a %u encoded version of the string, suitable for urls
- [bool](#type-bool) `NotNULLOrEmpty`: TRUE if the string is not empty and does not contain the literal NULL. This provides a shortcut for: <tt>if ${MyString.Length} &amp;&amp; !${MyString.Equals[NULL]}</tt>
- [string](#type-string) `AsJSON`: Returns a JSON encoded version of the string, including surrounding quotes
- [string](#type-string) `Trim`: Returns a copy of the string with no leading or trailing whitespace
- [string](#type-string) `ReplaceSubstring[` [string](#type-string) `needle` `]`
- [string](#type-string) `ReplaceSubstring[` [string](#type-string) `haystack` `]`
- [string](#type-string) `ReplaceSubstring[` `needle` `,` `replacement` `]`: Performs in-place replacement of a needle in a haystack. For example, <tt>${String[abcdefg].ReplaceSubstring[def,xyz]}</tt> is <tt>abcxyzg</tt>
- [string](#type-string) `StartsWith`
- [string](#type-string) `EndsWith`

### Methods
none.
### Static Members
- [bool](#type-bool) `Equal[` [string](#type-string) `A` `,` [string](#type-string) `B` `]`: Tests equality (case insensitive) of two strings
- [bool](#type-bool) `IsNULLOrEmpty[` [string](#type-string) `str` `]`: Determines if a string is NULL or empty
- [bool](#type-bool) `IsNULLOrWhitespace[` [string](#type-string) `str` `]`: Determines if a string is NULL or empty/whitespace



## Type: rgb
- Persistent: No ([weakref](#type-weakref) not supported)

As Text: Same as `Hex`

### Members
- [byte](#type-byte) `Red`: 0-255 indicating the amount of red
- [byte](#type-byte) `Green`: 0-255 indicating the amount of green
- [byte](#type-byte) `Blue`: 0-255 indicating the amount of blue
- [string](#type-string) `Hex`: A hexadecimal value representing the color, in the form rrggbb.  For example, "ff0000" is full red.

### Methods
- `Set[` [string](#type-string) `hexValue` `]`
- `Set`: Sets the rgb hex to a given value



## Type: byte
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `byte[` <[byte](#type-byte) `value`=0> `]`

### Members
- [byte](#type-byte) `Inc[` <[byte](#type-byte) `expression`=1> `]`: Returns this byte, plus a given amount
- [byte](#type-byte) `Dec[` <[byte](#type-byte) `expression`=1> `]`: Returns this byte, minus a given amount
- [bool](#type-bool) `Between[` [byte](#type-byte) `,` [byte](#type-byte) `]`
- ??? `Equal[`???`]`

### Methods
- `Inc[` <[byte](#type-byte) `expression`=1> `]`: Increments this byte by a given amount
- `Inc`: Increments this byte by 1
- `Dec[` <[byte](#type-byte) `expression`=1> `]`: Decrements this byte by a given amount
- `Dec`: Decrements this bye by 1
- `Set[` [byte](#type-byte) `expression` `]`: Sets this bye to a given value

### Static Members
- [byte](#type-byte) `Min`
- [byte](#type-byte) `Max`



## Type: bool
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `bool[` <[bool](#type-bool) `value`=false> `]`

As Text: TRUE (non-zero) or FALSE (zero)

### Members
- [bool](#type-bool) `Equal[` [bool](#type-bool) `expression` `]`: TRUE if the boolean value matches the boolean result of the calculation (zero is FALSE, non-zero is TRUE)
- [bool](#type-bool) `Not`: Gives the opposite value, e.g. if the value is TRUE, Not is FALSE
- [string](#type-string) `AsJSON`: A string containing true or false as would be specified in JSON

### Methods
- `Toggle`: Toggles between TRUE and FALSE
- `Set[` [bool](#type-bool) `expression` `]`: Sets this bool to a specific value



## Type: unistring
- Base Type: [string](#type-string)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- [string](#type-string) `String`

### Methods
none.


## Type: mutablestring
- Base Type: [string](#type-string)
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `mutablestring[` <[string](#type-string) `value`=""> `]`

### Members
- [string](#type-string) `String`: Retrieves the appropriate string object from this mutablestring

### Methods
- `Set`
- `Set[` [string](#type-string) `newValue` `]`: Sets the value of the string to this new text
- `Concat[` [string](#type-string) `value` `]`: Concatenates the string with this new text
- `ToUpper`: Converts the string to upper case
- `ToLower`: Converts the string to lower case
- `Prepend[` [string](#type-string) `value` `]`



## Type: float
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `float[` <[float](#type-float) `value`=0.0> `]`


### Members
- [float](#type-float) `Inc[` <[float](#type-float) `expression`=1.0> `]`: Returns this float, plus a given amount
- [float](#type-float) `Dec[` <[float](#type-float) `expression`=1.0> `]`: Returns this float, minus a given amount
- [float](#type-float) `Mul[` [float](#type-float) `expression` `]`: Returns this float, multiplied by a given amount
- [float](#type-float) `Div[` [float](#type-float) `expression` `]`: Returns this float, divided by a given amount
- [string](#type-string) `Deci`: The value of this float, to the nearest tenth
- [string](#type-string) `Centi`: The value of this float, to the nearest hundredth
- [string](#type-string) `Milli`: The value of this float, to the nearest thousandth
- [int64](#type-int64) `Int`: The value of this float, to its largest whole number (e.g. for 1.9 this is 1, for -0.1, this is -1)
- [string](#type-string) `Precision[` [int](#type-int) `numPlaces` `]`: The value of this float, to the nearest # decimal places (e.g. 1 is tenths, 2 is hundredths, 3 is thousandths, and so on)
- [int64](#type-int64) `Ceil`: The value of this float, to its largest partial number (e.g. for 1.1 this is 2, for -0.1 this is 0).
- [int](#type-int) `Round`: The value of this float, rounded to the nearest whole number
- [bool](#type-bool) `Equal[` [float](#type-float) `expression` `]`: TRUE if the float matches the specified value
- [string](#type-string) `AsJSON`: A string with the value of the float, as would be in JSON
- [bool](#type-bool) `Between[` [float](#type-float) `minInclusive` `,` [float](#type-float) `maxInclusive` `]`: TRUE if   a<= value and value <= b

### Methods
- `Inc[` <[float](#type-float) `expression`=1.0> `]`: Increments this float by a given amount
- `Inc`: Increments this float by 1.0
- `Dec[` <[float](#type-float) `expression`=1.0> `]`: Decrements this float by a given amount
- `Dec`: Decrements this float by 1.0
- `Mul[` [float](#type-float) `expression` `]`: Multiplies this float by a given amount
- `Div[` [float](#type-float) `expression` `]`: Divides this float by a given amount
- `Set[` [float](#type-float) `expression` `]`: Sets this float to a given value

### Static Members
- [float](#type-float) `Min`
- [float](#type-float) `Max`



## Type: int64
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `int64[` <[int64](#type-int64) `value`=0> `]`


### Members
- [int64](#type-int64) `Inc[` <[int64](#type-int64) `expression`=1> `]`: Returns this int64, plus a given amount
- [int64](#type-int64) `Dec[` <[int64](#type-int64) `expression`=1> `]`: Returns this int64, minus a given amount
- [int64](#type-int64) `Mul[` [int64](#type-int64) `expression` `]`: Returns this int64, multiplied by a given amount
- [int64](#type-int64) `Div[` [int64](#type-int64) `expression` `]`: Returns this int64, multiplied by a given amount
- [float](#type-float) `Float`: This number, converted to a float (NOTE: Float is only accurate to 32 bits of precision)
- [string](#type-string) `Hex`: A hexadecimal string equivalent to this number
- [string](#type-string) `LeadingZeroes[` `#` `]`: A string representation of this number, with at least this many decimal places.  The number will be lead with zeroes to reach the desired length
- [bool](#type-bool) `Between[` [int64](#type-int64) `,` [int64](#type-int64) `]`: TRUE if   a<= value and value <= b
- [bool](#type-bool) `Equal[` [formula](#type-formula) `]`: TRUE if the int64 matches the specified value
- [string](#type-string) `AsJSON`: A string with the value of the int64, as would be in JSON

### Methods
- `Inc[` <[int64](#type-int64) `expression`=1> `]`: Increments this int64 by a given amount
- `Inc`: Increments this int64 by 1
- `Dec[` <[int64](#type-int64) `expression`=1> `]`: Decrements this int64 by a given amount
- `Dec`: Decrements this int64 by 1
- `Mul[` [int64](#type-int64) `expression` `]`: Multiplies this int64 by a given amount
- `Div[` [int64](#type-int64) `expression` `]`: Divides this int64 by a given amount
- `Set[` [int64](#type-int64) `expression` `]`: Sets this int64 to a given value

### Static Members
- [int64](#type-int64) `Min`
- [int64](#type-int64) `Max`



## Type: float64
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `float64[` <[float64](#type-float64) `value`=0.0> `]`


### Members
- [float64](#type-float64) `Inc[` <[float64](#type-float64) `expression`=1> `]`: Returns this float64, plus a given amount
- [float64](#type-float64) `Dec[` <[float64](#type-float64) `expression`=1> `]`: Returns this float64, minus a given amount
- [float64](#type-float64) `Mul[` [float64](#type-float64) `expression` `]`: Returns this float64, multiplied by a given amount
- [float64](#type-float64) `Div[` [float64](#type-float64) `expression` `]`: Returns this float64, divided by a given amount
- [string](#type-string) `Deci`: The value of this float, to the nearest tenth
- [string](#type-string) `Centi`: The value of this float, to the nearest hundredth
- [string](#type-string) `Milli`: The value of this float, to the nearest thousandth
- [int64](#type-int64) `Int`: The value of this float, to its largest whole number (e.g. for 1.9 this is 1, for -0.1, this is -1)
- [string](#type-string) `Precision[` [int](#type-int) `numPlaces` `]`: The value of this float, to the nearest # decimal places (e.g. 1 is tenths, 2 is hundredths, 3 is thousandths, and so on)
- [int64](#type-int64) `Ceil`: The value of this float, to its largest partial number (e.g. for 1.1 this is 2, for -0.1 this is 0).
- [int](#type-int) `Round`: The value of this float, rounded to the nearest whole number
- [bool](#type-bool) `Equal[` [float](#type-float) `expression` `]`: TRUE if the float64 matches the specified value
- [string](#type-string) `AsJSON`: A string with the value of the float64, as would be in JSON
- [bool](#type-bool) `Between[` [float64](#type-float64) `minInclusive` `,` [float64](#type-float64) `maxInclusive` `]`: TRUE if   a<= value and value <= b

### Methods
- `Inc[` <[float64](#type-float64) `expression`=1> `]`: Increments this float64 by a given amount
- `Inc`: Increments this float64 by 1.0
- `Dec[` <[float64](#type-float64) `expression`=1> `]`: Decrements this float64 by a given amount
- `Dec`: Decrements this float64 by 1.0
- `Mul[` [float64](#type-float64) `expression` `]`: Multiplies this float64 by a given amount
- `Div[` [float64](#type-float64) `expression` `]`: Divides this float64 by a given amount
- `Set[` [float64](#type-float64) `expression` `]`: Sets this float64 to a given value

### Static Members
- [float64](#type-float64) `Min`
- [float64](#type-float64) `Max`



## Type: floatptr
- Base Type: [float](#type-float)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: float64ptr
- Persistent: No ([weakref](#type-weakref) not supported)


### Members
- [float64](#type-float64) `Inc[` <[float64](#type-float64) `expression`=1> `]`: Returns this float64, plus a given amount
- [float64](#type-float64) `Dec[` <[float64](#type-float64) `expression`=1> `]`: Returns this float64, minus a given amount
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
- Base Type: [string](#type-string)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: uintptr
- Base Type: [uint](#type-uint)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: intptr
- Base Type: [int](#type-int)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: int64ptr
- Persistent: No ([weakref](#type-weakref) not supported)


### Members
- [int64](#type-int64) `Inc[` <[int64](#type-int64) `expression`=1> `]`: Returns this int64, plus a given amount
- [int64](#type-int64) `Dec[` <[int64](#type-int64) `expression`=1> `]`: Returns this int64, minus a given amount
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
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: byteptr
- Base Type: [byte](#type-byte)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: boolptr
- Base Type: [bool](#type-bool)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Address[`???`]`

### Methods
none.


## Type: math
- Static: Yes (All Members/Methods also work as Static Members/Methods)

### Members
- [float](#type-float) `Abs[` [float](#type-float) `value` `]`: Returns the absolute value of a given formula
- [uint](#type-uint) `Rand[` [uint](#type-uint) `range` `]`: Returns a random number from 0 to # - 1, where # is the result of the given formula. The maximum value that can be returned is 32767.
- [float64](#type-float64) `Calc[` [float64](#type-float64) `expression` `]`: Returns the result of a given formula
- [float](#type-float) `Sin[` [float64](#type-float64) `expression` `]`: Returns the sine of a given formula in degrees
- [float](#type-float) `Cos[` [float64](#type-float64) `expression` `]`: Returns the cosine of a given formula in degrees
- [float](#type-float) `Tan[` [float64](#type-float64) `expression` `]`: Returns the tangent of a given formula in degrees
- [float](#type-float) `Asin[` [float64](#type-float64) `expression` `]`: Returns the asin of a given formula in degrees (<tt>asin(sin(x))=x</tt>)
- [float](#type-float) `Acos[` [float64](#type-float64) `expression` `]`: Returns the acos of a given formula in degrees (<tt>acos(cos(x))=x</tt>)
- [float](#type-float) `Atan[` [float64](#type-float64) `expression` `]`: Returns the atan of a given formula in degrees (<tt>atan(tan(x))=x</tt>)
- [float](#type-float) `Atan[` [float64](#type-float64) `expression1` `,` [float64](#type-float64) `expression2` `]`: Returns the atan2 of two given formulae in degrees
- [string](#type-string) `Hex[` [int](#type-int) `value` `]`: Returns a hexadecimal string equivalent to the #
- [int](#type-int) `Dec[` [string](#type-string) `hexValue` `]`: Returns the decimal equivalent to the hexadecimal value given
- [int](#type-int) `Not[` [int](#type-int) `value` `]`: Returns the bitwise NOT of the #
- [float](#type-float) `Distance[` [float](#type-float) `X1` `,` [float](#type-float) `X2` `]`: Returns the 1-dimensional distance between x1 and x2
- [float](#type-float) `Distance[` [float](#type-float) `X1` `,` [float](#type-float) `Y1` `,` [float](#type-float) `X2` `,` [float](#type-float) `Y2` `]`: Returns the 2-dimensional distance between x1,y1 and x2,y2
- [float](#type-float) `Distance[` [float](#type-float) `X1` `,` [float](#type-float) `Y1` `,` [float](#type-float) `Z1` `,` [float](#type-float) `X2` `,` [float](#type-float) `Y2` `,` [float](#type-float) `Z2` `]`: Returns the 3-dimensional distance between x1,y1,z1 and x2,y2,z2
- [float](#type-float) `Sqrt[` [float64](#type-float64) `expression` `]`: Returns the square root of a given formula
- [int64](#type-int64) `Calc64[` [int64](#type-int64) `expression` `]`: Returns the result of a given formula with 64-bit integer precision
- [float](#type-float) `DistancePointLine[` [float](#type-float) `pointX` `,` [float](#type-float) `pointY` `,` [float](#type-float) `segmentStartX` `,` [float](#type-float) `segmentStartY` `,` [float](#type-float) `segmentEndX` `,` [float](#type-float) `segmentEndY` `]`: Returns the distance from x,y to the nearest point on the line from a and b, or NULL if the perpendicular passing through point (x,y) to the line defined by (ax,ay) (bx,by) does not intersect on the segment between points a and b.
- [float](#type-float) `Log[` [float64](#type-float64) `expression` `]`

### Methods
none.


## Type: type
- Persistent: No ([weakref](#type-weakref) not supported)

As Text: Same as `Name`

### Members
- [string](#type-string) `Name`: Name of the data type
- [string](#type-string) `Member[` [uint](#type-uint) `id` `]`
- [uint](#type-uint) `Member[` [string](#type-string) `name` `]`
- [string](#type-string) `Method[` [uint](#type-uint) `id` `]`
- [uint](#type-uint) `Method[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `Members`
- [jsonarray](#type-jsonarray) `Methods`
- [bool](#type-bool) `Static`
- [jsonarray](#type-jsonarray) `StaticMembers`
- [jsonarray](#type-jsonarray) `StaticMethods`
- [type](#type-type) `Inherits`
- [type](#type-type) `VariableType`
- [string](#type-string) `PersistentClass`
- [jsonobject](#type-jsonobject) `Metadata`
- [jsonobject](#type-jsonobject) `AsJSON`
- ??? `Create[`???`]`

### Methods
none.
### Static Members
- [type](#type-type) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))



## Type: time
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `time[` <[int](#type-int) `timestamp`=0> `]`

As Text: Same as `Time24`

### Members
- [intptr](#type-intptr) `Hour`: Hour of the day (0-23)
- [intptr](#type-intptr) `Minute`: Minute of the hour (0-59)
- [intptr](#type-intptr) `Second`: Second of the minute (0-59)
- [uint](#type-uint) `DayOfWeek`: Day of the week (1-7)
- [intptr](#type-intptr) `Day`: Day of the month (1-31 depending on the month)
- [uint](#type-uint) `Month`: Month of the year (1-12)
- [uint](#type-uint) `Year`: Year
- [string](#type-string) `Time12`: Time in hh:mm:ss given in 12-hour format
- [string](#type-string) `Time24`: Time in hh:mm:ss given in 24-hour format
- [string](#type-string) `Date`: Date in mm/dd/yyyy
- [bool](#type-bool) `Night`: TRUE if current time is after 7pm and before 7am
- [uint](#type-uint) `SecondsSinceMidnight`: Number of seconds since midnight
- [uint](#type-uint) `Timestamp`: Number of seconds since epoch (standard UNIX timestamp)
- [intptr](#type-intptr) `DayOfWeekPtr`: Day of the week (0-6) - Mainly useful for *setting*
- [intptr](#type-intptr) `MonthPtr`: Month of the year (0-11) - Mainly useful for *setting*
- [intptr](#type-intptr) `YearPtr`: Year-1900 (e.g. 0 is 1900, 100 is 2000) - Mainly useful for *setting*

### Methods
- `Set[` [int](#type-int) `timestamp` `]`: Sets the value based on the given timestamp (standard UNIX timestamp, number of seconds since epoch)
- `Update`: Updates the type after setting an individual member (NOT needed when using the Set method)

### Static Members
- [time](#type-time) `Now`



## Type: array
- Base Type: [objectcontainer](#type-objectcontainer)
- Persistent: No ([weakref](#type-weakref) not supported)


### Members
- [uint](#type-uint) `Dimensions`: Total number of extents of the array (e.g. 2-dimensional has two extents)
- [uint](#type-uint) `Size[` <[uint](#type-uint) `numDimension`> `]`: Total number of elements in a given dimension of the array
- [uint](#type-uint) `Size`: Total number of elements in the array, including all dimensions
- [mutablestring](#type-mutablestring) `Expand`
- [mutablestring](#type-mutablestring) `Expand[` [begin](#type-begin) `#` `,` `length` `]`: Retrieves the text representation of each object in the array as quoted parameters, separated by spaces.  If no parameters are given to Expand, the entire array will be used.  If only the begin # is used, the rest of the array, beginning with the element # specified, will be used.  If the length is additionally given, that number of elements from the array will be used, beginning with the element # specified as the beginning.
- [mutablestring](#type-mutablestring) `ExpandComma`
- [mutablestring](#type-mutablestring) `ExpandComma[` [begin](#type-begin) `#` `,` `length` `]`: Retrieves the text representation of each object in the array as quoted parameters, separated by commas.  If no parameters are given to Expand, the entire array will be used.  If only the begin # is used, the rest of the array, beginning with the element # specified, will be used.  If the length is additionally given, that number of elements from the array will be used, beginning with the element # specified as the beginning.
- [unistring](#type-unistring) `AsJSON[` <"multiline"> `]`
- [unistring](#type-unistring) `AsJSON`: Returns a JSON array representation of this array, with each element converted by using its AsJSON member

### Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: For each element in the array, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration (filterQuery: see JSON definition [select](#definition-select))



## Type: system
- Static: Yes (All Members/Methods also work as Static Members/Methods)
- Persistent: No ([weakref](#type-weakref) not supported)


### Members
- [string](#type-string) `OS`: Operating system identifier (e.g. Microsoft Windows XP)
- [uint](#type-uint) `MemFree`: Amount of free physical system RAM, in megabytes
- [uint](#type-uint) `MemTotal`: Total amount of physical system RAM, in megabytes
- [string](#type-string) `OSBuild`: Operating system build identifier (e.g. 2600.xpsp_sp2_rtm040803-2158)
- [uint](#type-uint) `GetProcAddress[` `module` `,` `function` `]`: Retrieves the address of an exported function, usually in a DLL. (Level of understanding: High)
- [uint](#type-uint) `TickCount`: A timestamp given in milliseconds.  This value does "wrap" every 46 days or so.
- ??? `GetCurrentDirectory[`???`]`
- [uint](#type-uint) `MemoryUsage`: Amount of memory used by this process (the uplink or session), in bytes
- ??? `APICall[`???`]`
  - Restricted: Yes
- ??? `Processors[`???`]`
- ??? `ClipboardText[`???`]`
- ??? `ProcessID[`???`]`
- [string](#type-string) `RegistryValue[` "hklm"|"hkcu" `,` `key` `,` `value` `]`: Retrieve a REG_DWORD, REG_SZ, or REG_EXPAND_SZ value from the system registry
- [unistring](#type-unistring) `EnvironmentVariable[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `EnvironmentVariables`
- [unistring](#type-unistring) `ExpandEnvironmentStrings[` [string](#type-string) `haystack` `]`

### Methods
- `SetEnvironmentVariable`
- `SetEnvironmentVariable[` [string](#type-string) `name` `,` [string](#type-string) `value` `]`
- `CreateShortcut[` [jsonobject](#type-jsonobject) `json` `]`
- `APICall[`???`]`
  - Restricted: Yes
- `SetClipboardText[`???`]`
- `LoadDLL[` [string](#type-string) `filePath` `,` <"+imports"|"+exports"|"+direct"|"+disable"|"-imports"|"-exports"|"-direct"|"-disable"> `]`
- `DebugBreak`
- `DebugOutput[` [string](#type-string) `text` `]`
- `ShowMessageBox[` [string](#type-string) `text` `,` [string](#type-string) `caption` `]`



## Type: point3f
- Persistent: No ([weakref](#type-weakref) not supported)



### Members
- [floatptr](#type-floatptr) `X`: X coordinate
- [floatptr](#type-floatptr) `Y`: Y coordinate
- [floatptr](#type-floatptr) `Z`: Z coordinate
- [string](#type-string) `XYZ`: concatenated XYZ string, separated by commas
- [string](#type-string) `XYZ[` `#` `]`: concatenated XYZ string, separated by given field separator character
- ??? `Adjust[`???`]`
- ??? `Distance[`???`]`
- ??? `DistancePointLine[`???`]`

### Methods
- `Set[` `X` `]`: Sets x to a given value
- `Set[` `X` `,` `Y` `]`: Sets x,y to a given value
- `Set[` `X` `,` `Y` `,` `Z` `]`: Sets x,y,z to a given value
- `Adjust[`???`]`



## Type: lavishscript
- Static: Yes (All Members/Methods also work as Static Members/Methods)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- [string](#type-string) `Version`: LavishScript version number (e.g. 1.07)
- [filepath](#type-filepath) `CurrentDirectory`: Current directory according to LavishScript
- [int](#type-int) `RunningTime`: Amount of time, in milliseconds, the current application has been running.  This value wraps after about 23 days of leaving the application running.
- [filepath](#type-filepath) `HomeDirectory`: Home directory according to LavishScript
- [string](#type-string) `LSModule`: LavishScript version number
- [string](#type-string) `ExecuteAtom[` `name` `,` ... [string](#type-string) `]`: Executes an atom with the given name in global- or script-scope (if a script is currently in context).  Extra parameters are passed as parameters to the atom.  If the atom returns a value, this will be the string given.
- [filepath](#type-filepath) `Executable`: Executable filename for the current process
- ??? `CommandLine[`???`]`
- [variablescope](#type-variablescope) `VariableScope`: The global variable scope
- [uint](#type-uint) `CreateQuery[` [string](#type-string) `expression` `]`: ([[LavishScript:Object Queries|Object Queries]]) Creates a query with the given expression -- e.g. ${LavishScript.CreateQuery[Name=="Bonkers"]}
- [string](#type-string) `RetrieveQueryExpression[` [uint](#type-uint) `queryID` `]`: ([[LavishScript:Object Queries|Object Queries]]) Retrieves the query expression for a previously created query, by ID
- [bool](#type-bool) `QueryEvaluate[` [uint](#type-uint) `queryID` `,` [weakref](#type-weakref) `object` `]`: ([[LavishScript:Object Queries|Object Queries]]) Determines if the given object matches the given query
- [bool](#type-bool) `SelectEvaluate[` [weakref](#type-weakref) `object` `,` [jsonvalueref](#type-jsonvalueref) `joSelect` `]`: (joSelect: see JSON definition [select](#definition-select))
- ??? `Is64Bit[`???`]`
- ??? `MetaScript[`???`]`
- ??? `MetaScripts[`???`]`
- ??? `LoadMetaScript[`???`]`
- ??? `LoadMetaScriptJSON[`???`]`
- [jsonarray](#type-jsonarray) `Aliases`
- [jsonarray](#type-jsonarray) `Commands`
- [jsonarray](#type-jsonarray) `Events`
- [jsonarray](#type-jsonarray) `Scripts`
- [jsonarray](#type-jsonarray) `TopLevelObjects`
- [jsonarray](#type-jsonarray) `Types`
- [string](#type-string) `LastError`
- [bool](#type-bool) `LastErrorSpam`
- [anonevent](#type-anonevent) `OnSetLastError`

### Methods
- `Echo[` ... [string](#type-string) `lines` `]`
- `ExecuteAtom[` [string](#type-string) `name` `,` ... [string](#type-string) `]`: Executes an atom with the given name in global- or script-scope (if a script is currently in context).  Extra parameters are passed as parameters to the atom.
- `RegisterEvent[` [string](#type-string) `name` `]`: Registers an event of <name>
- `RegisterAlias[`???`]`
- `LoadModule[`???`]`
- `Eval[` [string](#type-string) `command` `,` [weakref](#type-weakref) `index:string` `]`: Evaluates the given command, directing any lines of output into an index:string
- `RegisterEnum[` [string](#type-string) `typeName` `,` <[bool](#type-bool) `isFlags`=false> `]`: Registers a new enum and LavishScript Object Type with <typeName>. An optional second parameter controls whether the enum is flags, meaning that multiple values may be combined as part of the same value -- if not provided, the default is FALSE. After registering, value names can be added to the enum type via the Enum TLO
- `LoadMetaScript[`???`]`
- `LoadMetaScriptJSON[`???`]`
- `SetLastError[` <[string](#type-string) `value`=""> `]`
- `SetLastErrorSpam[` [bool](#type-bool) `value` `]`



## Type: script

### Members
- ??? `ID[`???`]`
- [string](#type-string) `Filename`: Filename of this script
- [variable](#type-variable) `Variable[` `name` `]`: A given script-scope variable
- [int](#type-int) `RunningTime`: Number of milliseconds since this script began
- [filepath](#type-filepath) `CurrentDirectory`: Current working directory for this script
- [bool](#type-bool) `Paused`: Scripts current paused state
- [bool](#type-bool) `Profiling`: Profiling status true/false. Debugging must be allowed for profiling to be on.
- [bool](#type-bool) `AllowDebug`: If debugging is allowed
- [string](#type-string) `ExecuteAtom[` `name` `,` ... [string](#type-string) `]`: Executes an atom in script-scope with the given name.  Any extra parameters are passed as parameters to the atom.  If the atom returns a value, the value is given.
- [variablescope](#type-variablescope) `VariableScope`: The scripts variable scope
- ??? `Turbo[`???`]`
- [metascript](#type-metascript) `MetaScript`
- [bool](#type-bool) `Retain`
- [function](#type-function) `Function[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `Functions`
- [jsonarray](#type-jsonarray) `Atoms`
- [scriptobjecttype](#type-scriptobjecttype) `ObjectDef[` [string](#type-string) `typeName` `]`: Retrieves a scriptobjecttype by name
- [jsonarray](#type-jsonarray) `ObjectDefs`
- [string](#type-string) `LastError`
- [bool](#type-bool) `LastErrorSpam`
- [anonevent](#type-anonevent) `OnSetLastError`
- [anonevent](#type-anonevent) `OnExit`
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `End`: Ends execution of this script
- `Squelch`: Squelches most output from this script (excluding most errors and generally excluding Echo)
- `Unsquelch`: Unsquelches
- `QueueCommand[` `command` `]`: Inserts a command in the scripts command queue
- `Pause`: Pauses this script
- `Resume`: Resumes this script
- `ExecuteAtom[` `name` `,` ... [string](#type-string) `]`: Executes an atom in script-scope with the given name.  Any extra parameters are passed as parameters to the atom.
- `EnableProfiling`: Enables script profiling. Debugging must be turned on to enable.
- `DisableProfiling`: Disables script profiling.
- `DisableDebugging`: Disables debugging.
- `DumpStack`: Dumps the current stack into the console.
- `DumpProfiling`: Dumps the entire script into the console.
- `EnableDebugLogging[` `filename` `]`: Enables full debug logging to file.
- `DisableDebugLogging`: Disables full debug logging
- `SetLastError[` <[string](#type-string) `value`=""> `]`
- `SetLastErrorSpam[` [bool](#type-bool) `value` `]`
- `SetRetain[` [bool](#type-bool) `value` `]`
- `Turbo[`???`]`

### Static Members
- [script](#type-script) `New[` [string](#type-string) `full_filename` `,` <... [string](#type-string) `script_params`> `]`
- [script](#type-script) `Get[` [string](#type-string) `filename` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))
- [anonevent](#type-anonevent) `OnScriptStarted`
- [anonevent](#type-anonevent) `OnScriptStopped`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))



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
- Base Type: [unistring](#type-unistring)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- [bool](#type-bool) `IsDirectory[` <[string](#type-string) `appendPath`> `]`: TRUE if that's a folder
- [bool](#type-bool) `PathExists`: TRUE if the given path exists
- [bool](#type-bool) `FileExists[` [string](#type-string) `additionalPath` `]`: TRUE if the given additional path exists.  This can be a directory OR file, and can be an absolute path or a path relative to this filepath
- [unistring](#type-unistring) `Path`: The unistring representation of this path
- [unistring](#type-unistring) `PathOnly`: The unistring representation of this path, minus the filename (portion after last /)
- [unistring](#type-unistring) `FilenameOnly`: The unistring representation of the filename, minus the path (portion before last /)
- [unistring](#type-unistring) `AbsolutePath`: The unistring representation of this path converted to an absolute path
- [jsonarray](#type-jsonarray) `GetFiles[` <[string](#type-string) `wildcard`="*"> `]`
- [jsonarray](#type-jsonarray) `GetDirectories[` <[string](#type-string) `wildcard`="*"> `]`

### Methods
none.
### Static Members
- [filepath](#type-filepath) `Get[` [string](#type-string) `filePath` `]`



## Type: mutablefilepath
- Base Type: [mutablestring](#type-mutablestring)
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `mutablefilepath[` <[string](#type-string) `value`=""> `]`

As Text: Same as `Path`

### Members
- [bool](#type-bool) `IsDirectory[` <[string](#type-string) `appendPath`> `]`: TRUE if that's a folder
- [bool](#type-bool) `PathExists`: TRUE if the given path exists
- [bool](#type-bool) `FileExists[` [string](#type-string) `additionalPath` `]`: TRUE if the given additional path exists.  This can be a directory OR file, and can be an absolute path or a path relative to this filepath
- [string](#type-string) `Path`: The string representation of this path
- [string](#type-string) `PathOnly`: The string representation of this path, minus the filename (portion after last /)
- [string](#type-string) `FilenameOnly`: The string representation of the filename, minus the path (portion before last /)
- [string](#type-string) `AbsolutePath`: The path, converted if necessary to an absolute path
- [jsonarray](#type-jsonarray) `GetFiles[` <[string](#type-string) `wildcard`="*"> `]`
- [jsonarray](#type-jsonarray) `GetDirectories[` <[string](#type-string) `wildcard`="*"> `]`

### Methods
- `Set[` [string](#type-string) `value` `]`: Sets the path to the a value
- `MakeAbsolute`: Sets the path to its Absolute value
- `MakeSubdirectory[` [string](#type-string) `Sub-directory name` `]`



## Type: file
- Persistent: No ([weakref](#type-weakref) not supported)

### Initializers
- `file[` <[string](#type-string) `filePath`=""> `]`


### Members
- [bool](#type-bool) `Open`: TRUE if the file is open
- [filepath](#type-filepath) `Path`: Full path to this file
- [string](#type-string) `Filename`: Filename of this file
- [string](#type-string) `Read`: Reads a line from this file, up to 1024 characters long (result includes carriage return)
- [string](#type-string) `Read[` `#` `]`: Reads a line from this file, up to # characters long (result includes carriage return)
- [int](#type-int) `ReadBinary[` [binary](#type-binary) `variable` `,` `#` `]`: Reads # bytes into the specified buffer. Result is the number of bytes read.
- [int](#type-int) `Position`: Current position within the file
- [int](#type-int) `Size`: Size of the file
- [bool](#type-bool) `EOF`: TRUE if the previous Read or ReadBinary hit the end of the file

### Methods
- `SetFilename[` `filename` `]`: Sets the full path and filename. Only valid while file is closed.
- `Open`: Opens the file in read-write mode. Creates the file if it does not exist.
- `Open[` `readonly` `]`: Opens the file in read-only mode. Does not create the file if it does not exist.
- `Close`: Closes the file
- `Write[` `text` `]`: Writes the given text to the file
- `WriteBinary[` [binary](#type-binary) `variable` `,` `#` `]`: Writes # bytes from the given buffer variable to the file
- `Seek[` `#` `]`: Seeks to the specified position within the file
- `SeekEnd`: Seeks to the end of the file
- `Skip[` `#` `]`: Skips # bytes within the file
- `Truncate`: Truncates the file at the current position (all data after this point in the file is removed)
- `Flush`: Forces any pending writes to disk.  Writes may otherwise be buffered until the file is closed, or if the file is open for both reading and writing, until a read operation
- `Copy[`???`]`
- `Delete[`???`]`
- `Rename[`???`]`



## Type: filelist
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- [int](#type-int) `Files`: Total file count
- [filelistentry](#type-filelistentry) `File[` `#` `]`: The filelistentry of file <#>

### Methods
- `GetFiles[` `*` `]`: Gets all files from the given directory. (Defaults to current directory and * for files.)
- `GetDirectories[` `*` `]`: Gets all directories from the given directory. (Defaults to current directory)
- `Reset`: Clears the filelist.



## Type: filelistentry
- Persistent: No ([weakref](#type-weakref) not supported)


### Members
- [string](#type-string) `Filename`: Name of the file
- [string](#type-string) `FullPath`: Path+Filename of the file
- [int64ptr](#type-int64ptr) `CreationTime`: Win32 FILETIME (number of 100-nanosecond intervals since January 1, 1601) value representing the time of creation of this file
- [int64ptr](#type-int64ptr) `LastWriteTime`: Win32 FILETIME (number of 100-nanosecond intervals since January 1, 1601) value representing the last time of modification of this file
- [int64ptr](#type-int64ptr) `LastAccessTime`: Win32 FILETIME (number of 100-nanosecond intervals since January 1, 1601) value representing the last time of acces of this file
- [int](#type-int) `Size`: Size in bytes of the file

### Methods
none.


## Type: binary
- Persistent: No ([weakref](#type-weakref) not supported)



### Members
- [intptr](#type-intptr) `Int[` `#` `]`: An int at byte position # of this buffer
- [byteptr](#type-byteptr) `Byte[` `#` `]`: A byte at position # of this buffer
- [floatptr](#type-floatptr) `Float[` `#` `]`: A float at byte position # of this buffer
- [int64ptr](#type-int64ptr) `Int64[` `#` `]`: An int64 at byte position # of this buffer
- [string](#type-string) `String[` `#` `]`: A string at byte position # of this buffer.  NULL if the string is not null-terminated within the size of the buffer
- [uintptr](#type-uintptr) `Uint[` `#` `]`: A uint at byte position # of this buffer
- [boolptr](#type-boolptr) `Bool[` `#` `]`: A bool at byte position # of this buffer
- [uint](#type-uint) `Size`: Size of the buffer

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
- [int](#type-int) `ID`: ID number of the event (used by modules)
- [string](#type-string) `Name`: Name of the event

### Methods
- `Clear`: Forcefully detach all atoms and C functions from this event
- `AttachAtom[` `name` `]`: Attach an atom to this event
- `DetachAtom[` `name` `]`: Detach an atom from this event
- `Unregister`: Unregister this event
- `Execute[` ... [string](#type-string) `]`: Execute this event, optionally with any number of parameters
- `ThisExecute[` `object` `,` ... [string](#type-string) `]`: Execute this event in the context of a given object, optionally with any number of parameters

### Static Members
- [event](#type-event) `New[` [string](#type-string) `name` `]`
- [event](#type-event) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))



## Type: anonevent
- Base Type: [event](#type-event)
An anonymous event. Sort of like a masquerade, except it's a LavishScript event that has no Name or ID.

### Initializers
`anonevent`

### Members
none.
### Methods
none.


## Type: eventvar
- Base Type: [event](#type-event)
- Persistent: No ([weakref](#type-weakref) not supported)
Registers a named event for the lifetime of the eventvar. The named event will be unregistered when the eventvar is destroyed.

### Initializers
- `eventvar[` [string](#type-string) `eventName` `]`

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
- [string](#type-string) `Name`
- [string](#type-string) `Inherits`
- [string](#type-string) `PersistentClass`
- [bool](#type-bool) `Member[` [string](#type-string) `name` `]`
- [bool](#type-bool) `Method[` [string](#type-string) `name` `]`
- [bool](#type-bool) `Function[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `Members[` <[bool](#type-bool) `followIncludes`=true> `]`
- [jsonarray](#type-jsonarray) `Methods[` <[bool](#type-bool) `followIncludes`=true> `]`
- [variablescope](#type-variablescope) `VariableScope`: The Variable Scope containing static variables for this objectdef
- [bool](#type-bool) `Static`
- [jsonarray](#type-jsonarray) `StaticMembers[` <[bool](#type-bool) `followIncludes`=true> `]`
- [jsonarray](#type-jsonarray) `StaticMethods[` <[bool](#type-bool) `followIncludes`=true> `]`
- [jsonarray](#type-jsonarray) `Functions[` <[bool](#type-bool) `followIncludes`=true> `]`
- [jsonobject](#type-jsonobject) `Metadata`
- [jsonobject](#type-jsonobject) `AsJSON[` <[bool](#type-bool) `followIncludes`=true> `]`
- ??? `Create[`???`]`

### Methods
none.


## Type: scriptobjectref

### Members
none.
### Methods
none.


## Type: weakref
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Reference[`???`]`

### Methods
- `SetReference[`???`]`



## Type: objectcontainer

### Members
- [uint](#type-uint) `Size`: Number of objects the container may possibly contain in its present state
- [uint](#type-uint) `Used`: Number of objects presently contained

### Methods
- `Clear`: Clears all objects from the container
- `GetIterator[` [iterator](#type-iterator) `object` `]`: Initializes the given [[ObjectType:iterator|iterator]] object for iteration of this container



## Type: index
- Base Type: [objectcontainer](#type-objectcontainer)

### Members
- [uint](#type-uint) `Next[` `#` `]`: Retrieves the ID of the next valid element in the index, given an ID number
- [sub-type](#type-sub-type) `Get[` `#` `]`: Retrieves the #th element in the index
- [uint](#type-uint) `Insert[` ... [string](#type-string) `]`: Inserts an element in the index.  The parameters will be passed to the object initialization routine for the index sub-type, and an object will be created.  The returned value is the ID of the new element.  The index will be resized to fit the new object if necessary.
- [mutablestring](#type-mutablestring) `Expand[` [uint](#type-uint) `beginNum` `,` [uint](#type-uint) `length` `]`: Retrieves the text representation of each existing object in the index as quoted parameters, separated by spaces.  If no parameters are given to Expand, the entire index will be used.  If only the begin # is used, the rest of the index, beginning with the element # specified, will be used.  If the length is additionally given, that number of elements from the index will be used, beginning with the element # specified as the beginning.
- [mutablestring](#type-mutablestring) `ExpandComma[` [uint](#type-uint) `beginNum` `,` [uint](#type-uint) `length` `]`: Retrieves the text representation of each existing object in the index as quoted parameters, separated by commas.  If no parameters are given to Expand, the entire index will be used.  If only the begin # is used, the rest of the index, beginning with the element # specified, will be used.  If the length is additionally given, that number of elements from the index will be used, beginning with the element # specified as the beginning.
- [unistring](#type-unistring) `AsJSON`: Returns a JSON array representation of this index, with each element converted by using its AsJSON member
- [int64](#type-int64) `SelectKey[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [jsonarray](#type-jsonarray) `SelectKeys[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [object](#type-object) `SelectValue[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))

### Methods
- `Shift[` [uint](#type-uint) `position` `,` [uint](#type-uint) `places` `]`: Makes room for # places elements at # position, by shifting toward index.Size. The index will not be implicitly Resized, and elements at the end of the index may be destroyed.
- `Sort[`???`]`
- `Remove[` [uint](#type-uint) `id` `]`: Removes a single element from the index, by ID
- `RemoveByQuery[` [uint](#type-uint) `query_id` `]`: Erases any elements in the index matching the given [[LavishScript:Object_Queries|Query]]
- `RemoveByQuery[` [uint](#type-uint) `query_id` `,` [bool](#type-bool) `remove_MATCHES` `]`: Erases any elements in the index that either match or do not match the given [[LavishScript:Object_Queries|Query]]
- `Collapse`: Removes gaps in the index (from removal of elements) by shifting elements toward 1
- `Move[` `#` `,` `#` `]`: Moves an element to a new position in the index, by ID numbers.  If an element exists in the new position, it is destroyed
- `Swap[` `#` `,` `#` `]`: Swaps two positions in the index
- `Set[` `#` `,` ... [string](#type-string) `]`: Creates a new element in the index at the given position (destroying the previous element, if it existed).  The additional parameters will be passed to the object initialization routine for the index sub-type, and an object will be created.
- `Insert[` ... [string](#type-string) `]`: Inserts an element in the index.  The parameters will be passed to the object initialization routine for the index sub-type, and an object will be created.  The index will be resized to fit the new object if necessary.
- `Resize[` `#` `]`: Resizes the index such that it will hold at least this number of elements.
- `FromJSON[` <... [string](#type-string) `initializerParams`> `,` [string](#type-string) `JSON initializer` `]`: Initializes an index of objects from JSON. Each object must accept a JSON value.
- `NativeFromJSON[` <... [string](#type-string) `initializerParams`> `,` [string](#type-string) `JSON initializer` `]`: Initializes an index of objects from JSON. Each object must accept a native value.
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: For each element in the index, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration (filterQuery: see JSON definition [select](#definition-select))



## Type: collection
- Base Type: [objectcontainer](#type-objectcontainer)

### Members
- [sub-type](#type-sub-type) `Element[` [string](#type-string) `key` `]`: Retrieves the element, if any, identified by the given key
- [sub-type](#type-sub-type) `Get[` [string](#type-string) `key` `]`: Retrieves the element, if any, identified by the given key
- [sub-type](#type-sub-type) `FirstValue`: Begins iterating with an internal iterator, and retrieves the first value
- [sub-type](#type-sub-type) `NextValue`: Continues iterating with an internal iterator, retrieving the next value
- [string](#type-string) `FirstKey`: Begins iterating with an internal iterator, and retrieves the first key
- [string](#type-string) `NextKey`: Continues iterating with an internal iterator, retrieving the next key
- [string](#type-string) `CurrentKey`: Retrieves the current key in the iteration (with an internal iterator)
- [sub-type](#type-sub-type) `CurrentValue`: Retrieves the current value in the iteration (with an internal iterator)
- [jsonarray](#type-jsonarray) `Keys[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: A jsonarray of keys in the collection (filterQuery: see JSON definition [select](#definition-select))
- [unistring](#type-unistring) `AsJSON`: Returns a JSON object representation of this collection, with each element converted by using its AsJSON member. The keys from the collection will be used as keys in the JSON object
- [unistring](#type-unistring) `AsJSON[` "array" `]`: Returns a JSON array representation of this collection, with each element converted by using its AsJSON member.
- [string](#type-string) `SelectKey[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [jsonarray](#type-jsonarray) `SelectKeys[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [object](#type-object) `SelectValue[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))

### Methods
- `Set[` [string](#type-string) `key` `,` <... [array](#type-array) `initializer`> `]`: Sets (adding, if necessary) the element identified by the given key with the given value
- `FromJSON[` <... [string](#type-string) `initializerParams`> `,` [string](#type-string) `JSON initializer` `]`: Initializes a collection of objects from JSON. Each object must accept a JSON value.
- `NativeFromJSON[` <... [string](#type-string) `initializerParams`> `,` [string](#type-string) `JSON initializer` `]`: Initializes a collection of objects from JSON. Each object must accept a native value.
- `Erase[` `key` `]`: Erases the element, if any, identified by the given key
- `EraseByQuery[` [uint](#type-uint) `query_id` `]`: Erases any elements in the collection matching the given [[LavishScript:Object_Queries|Query]]
- `EraseByQuery[` [uint](#type-uint) `query_id` `,` [bool](#type-bool) `remove_MATCHES` `]`: Erases any elements in the collection that either match or do not match the given [[LavishScript:Object_Queries|Query]]
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: For each element in the collection, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration (filterQuery: see JSON definition [select](#definition-select))



## Type: stack
- Base Type: [objectcontainer](#type-objectcontainer)

### Members
- [sub-type](#type-sub-type) `Top`: Retrieves the first object in the stack

### Methods
- `Push[` ... [string](#type-string) `]`: Adds an object to the stack, passing any parameters to the initialization for the given object type
- `Pop`: Removes the first object in the stack



## Type: queue
- Base Type: [objectcontainer](#type-objectcontainer)

### Members
- [sub-type](#type-sub-type) `Peek`: Retrieves the first object in the queue (first in line)

### Methods
- `Queue[` ... [string](#type-string) `]`: Adds an object to the queue, passing any parameters to the initialization for the given object type
- `Dequeue`: Removes the first object in the queue



## Type: set
- Base Type: [objectcontainer](#type-objectcontainer)

### Members
- [bool](#type-bool) `Contains[` [string](#type-string) `key` `]`: TRUE if the given key exists in the set
- ??? `FirstKey[`???`]`
- ??? `NextKey[`???`]`
- ??? `CurrentKey[`???`]`
- [unistring](#type-unistring) `AsJSON`: Returns a JSON array representation of this array, with each element converted by using its AsJSON member

### Methods
- `Add[` [string](#type-string) `key` `]`: Adds a given key to the set
- `Remove[` [string](#type-string) `key` `]`: Removes a given key from the set
- `Erase[` [string](#type-string) `key` `]`: Removes a given key from the set
- `Merge[`???`]`
- `Intersect[` [set](#type-set) `A` `,` [set](#type-set) `B` `]`: Adds "sets A and intersect B" to this set
- `Union[` [set](#type-set) `A` `,` [set](#type-set) `B` `]`: Adds "set A union B" to this set
- `Not[` [set](#type-set) `A` `,` [set](#type-set) `B` `]`: Adds "set A not B" to this set
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: For each element in the set, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Value for each iteration (filterQuery: see JSON definition [select](#definition-select))



## Type: keyvaluepair
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Key[`???`]`
- ??? `Value[`???`]`

### Methods
none.


## Type: iterator
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- [object](#type-object) `Target`: The iteration target object (such as a set or collection being iterated).  The object type will be the original object type of the object
- [?](#type-?) `Key`: The current key in the iteration.  The object type depends on the data being iterated.
- [object](#type-object) `Value`: The current value in the iteration.  The object type depends on the data being iterated.
- [bool](#type-bool) `IsValid`: Determines if the iterator is valid, pointing to a valid iteration target and key/value
- [bool](#type-bool) `Reversible`: TRUE if the list being iterated also goes backwards, thus making the Previous method valid
- [bool](#type-bool) `Constant`: TRUE if the list will not allow you to set object values (i.e. the values are constant)
- [bool](#type-bool) `RandomAccess`: TRUE if the list allows random access (the iterator:Jump method)

### Methods
- `First`: Sets the iterator position to the first element
- `Last`: Sets the iterator position to the last element
- `Next`: Sets the iterator position to the next element (continues iteration forward)
- `Previous`: Sets the iterator position to the previous element (continues iteration backward)
- `JumpTo[` [string](#type-string) `key` `]`
- `SetValue[` [string](#type-string) `newValue` `]`: Sets the value at the current iterator position



## Type: variablescope

### Members
- [string](#type-string) `SelectKey[` [jsonvalueref](#type-jsonvalueref) `query` `]`
- [jsonarray](#type-jsonarray) `Keys[` [jsonvalueref](#type-jsonvalueref) `query` `]`
- [jsonarray](#type-jsonarray) `SelectKeys[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [object](#type-object) `SelectValue[` [object](#type-object) `query` `]`: (query: see JSON definition [select](#definition-select))
- [jsonobject](#type-jsonobject) `AsJSON`
- ??? `Create[` [string](#type-string) `typeName` `,` <... [array](#type-array) `initializerArgs`> `]`
- [int64](#type-int64) `Used`

### Methods
- `CreateVariable[` [object](#type-object) `type` `,` [string](#type-string) `name` `,` ... [string](#type-string) `]`: Creates a new variable in this scope of the given object type and name.  Any extra parameters are passed to object initialization
- `DeleteVariable[` [string](#type-string) `name` `]`: Deletes the variable in this scope with the given name, if any
- `Clear`: Deletes all variables within this scope
- `GetIterator[` [iterator](#type-iterator) `object` `]`: Initializes the given [[ObjectType:iterator|iterator]] object for iteration of this variable scope
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: For each variable in the scope, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration (filterQuery: see JSON definition [select](#definition-select))



## Type: enumtype
- Persistent: No ([weakref](#type-weakref) not supported)


### Members
- [string](#type-string) `Name`: Name of the enum type
- [int64](#type-int64) `ValueByName[` `name` `]`: Retrieves a value by its name
- [string](#type-string) `NameByValue[` `#` `]`: Retrieves a name by a given value (or for flags, a set of names from the combined value)
- [jsonarray](#type-jsonarray) `Names`
- [jsonarray](#type-jsonarray) `Values`
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `SetValue[` `name` `,` `#` `]`: Assigns a value to a given name
- `GetIterator[` [iterator](#type-iterator) `]`: Sets an iterator for iterating the available values

### Static Members
- [enumtype](#type-enumtype) `New[` [jsonvalueref](#type-jsonvalueref) `enumDefinition` `]`
- [enumtype](#type-enumtype) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` [jsonvalueref](#type-jsonvalueref) `filterQuery` `]`: (filterQuery: see JSON definition [select](#definition-select))

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))



## Type: enumvaluetype
All enum value types are an instance of this type

### Initializers
- `enumvaluetype[` [int64](#type-int64) `]`
- `enumvaluetype[` [string](#type-string) `]`

As Text: The Name(s) for the current value, if possible. Otherwise, the int64 value

### Members
- [int64](#type-int64) `Value`
- [string](#type-string) `Name`
- [enumtype](#type-enumtype) `Type`

### Methods
- `Set[` [int64](#type-int64) `]`
- `Set[` [string](#type-string) `]`

### Static Members
- [enumvaluetype](#type-enumvaluetype) `Get[` [string](#type-string) `]`
- [enumvaluetype](#type-enumvaluetype) `Get[` [int64](#type-int64) `]`
- [jsonarray](#type-jsonarray) `List[` [jsonvalueref](#type-jsonvalueref) `filterQuery` `]`: (filterQuery: see JSON definition [select](#definition-select))
- [jsonobject](#type-jsonobject) `EnumAsJSON`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))



## Type: jsonvalue

As Text: JSON representation of the value

### Members
- [string](#type-string) `AsString`: The contained value as a string
- [unistring](#type-unistring) `AsJSON[` <"multiline"> `]`: The contained value as multiline JSON text. multiline is literal, e.g. ${MyValue.AsJSON[multiline]}
- [string](#type-string) `AsJSON`: The contained value as single-line JSON text
- [string](#type-string) `Type`: The type of JSON object stored; one of: null, object, string, number, array, boolean, integer. Note that while the JSON standard does not differentiate between floating-point numbers and integers, LavishScript does
- [object](#type-object) `Value`: The contained value

### Methods
- `WriteFile[` [string](#type-string) `filePath` `,` <"multiline"> `,` <[string](#type-string) `lineSplit`="\\r\\n"> `]`: Writes the JSON to file, optionally in multi-line form, with a specified line splitter
- `WriteFile[` `filename` `]`: Writes the JSON to file, in condensed single-line form.
- `WriteFile[` `filename` `,` `multiline` `]`: Writes the JSON to file, optionally in multi-line form, with "\r\n" (Windows) line splitting

### Static Members
- [jsonvalue](#type-jsonvalue) `New[` <"-lazy"> `,` [string](#type-string) `json` `]`
- [jsonvalue](#type-jsonvalue) `ParseFile[` [filepath](#type-filepath) `filename` `]`



## Type: jsoniterator
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- [jsonvalue](#type-jsonvalue) `Target`
- ??? `Key`
- [jsonvalue](#type-jsonvalue) `Value`
- [bool](#type-bool) `IsValid`
- [bool](#type-bool) `Reversible`
- [bool](#type-bool) `Constant`
- [bool](#type-bool) `RandomAccess`

### Methods
- `First`
- `Last`
- `Next`
- `Previous`
- `JumpTo[` [string](#type-string) `key` `]`
- `SetValue[` [jsonvalue](#type-jsonvalue) `newValue` `]`



## Type: jsonvaluecontainer
- Base Type: [jsonvalue](#type-jsonvalue)

### Initializers
- `jsonvaluecontainer[` <[jsonvalue](#type-jsonvalue) `newValue`=null> `]`

As Text: JSON representation of the value

### Members
- [bool](#type-bool) `Equal[` [jsonvalueref](#type-jsonvalueref) `other` `]`
- [string](#type-string) `AsString`: The contained value as a string
- [unistring](#type-unistring) `AsJSON[` <"multiline"> `]`: The contained value as multiline JSON text
- [string](#type-string) `AsJSON`: The contained value as single-line JSON text
- [string](#type-string) `Type`: The type of JSON object stored; one of: null, object, string, number, array, true, false, integer. Note that while the JSON standard does not differentiate between floating-point numbers and integers, LavishScript does
- [jsonvaluecontainer](#type-jsonvaluecontainer) `Value`: The contained value

### Methods
- `SetValue[` <"-lazy"> `,` [jsonvalue](#type-jsonvalue) `newValue` `]`
- `SetValue[` `json` `]`: Sets the contained json value, e.g. myJsonValueContainer:SetValue["{\"someValue\":17}"] will set myJsonValueContainers value to a jsonobject that in turn contains one value
- `ParseFile[` [string](#type-string) `filename` `]`: Sets the contained json value to the contents of a specified json file
- `ParseINIFile[` [string](#type-string) `filename` `]`: Sets the contained json value to the contents of a specified INI file converted to json



## Type: jsonvalueref

### Initializers
- `jsonvalueref[` <[weakref](#type-weakref) `jsonValue`=null> `]`
- `jsonvalueref[` [jsonobject](#type-jsonobject) `json` `]`
- `jsonvalueref[` [jsonarray](#type-jsonarray) `json` `]`

As Text: JSON representation of the referenced value

### Members
- [jsonvalue](#type-jsonvalue) `Reference`

### Methods
- `SetReference[` [weakref](#type-weakref) `jsonValue` `]`



## Type: jsonarray

### Indexers
- [object](#type-object) `jsonarray[` ... [string](#type-string) `fieldPath` `]`

As Text: JSON representation of the array

### Members
- [bool](#type-bool) `Equal[` [jsonvalueref](#type-jsonvalueref) `jaOther` `]`
- [int64](#type-int64) `Contains[` [jsonvalue](#type-jsonvalue) `value` `]`: Returns the position of the first item found matching this value
- [int64](#type-int64) `ContainsReference[` [jsonvalueref](#type-jsonvalueref) `value` `]`: Returns the discovered position, if the jsonarray contains A REFERENCE TO THE SAME JSON VALUE (not just a matching value!)
- [jsonarray](#type-jsonarray) `Duplicate`: Returns a deep copy (completely new and separate clone) of the array
- [object](#type-object) `Get[` ... [string](#type-string) `fieldPath` `]`: Gets a value stored within this array, by its index (1-based)
- [object](#type-object) `Get[` `#` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonarrays and/or jsonobjects
- [object](#type-object) `Get[` <"-default" `,` [jsonvalue](#type-jsonvalue) `defaultValue`> `,` `#` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonarrays and/or jsonobjects, with a default value if not found
- [jsonvaluecontainer](#type-jsonvaluecontainer) `GetContainer[` ... [string](#type-string) `fieldPath` `]`: Gets a jsonvaluecontainer which holds a value within this array
- [jsonvaluecontainer](#type-jsonvaluecontainer) `GetContainer[` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a jsonvaluecontainer multiple levels deep within jsonobjects and/or jsonarrays
- [float64](#type-float64) `GetNumber[` ... [string](#type-string) `fieldPath` `]`: Gets a value stored within this array, by its index (1-based)
- [float64](#type-float64) `GetNumber[` `#` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonarrays and/or jsonobjects
- [float64](#type-float64) `GetNumber[` <"-default" `,` [jsonvalue](#type-jsonvalue) `defaultValue`> `,` `#` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonarrays and/or jsonobjects, with a default value if not found
- [int64](#type-int64) `GetInteger[` ... [string](#type-string) `fieldPath` `]`: Gets a value stored within this array, by its index (1-based)
- [int64](#type-int64) `GetInteger[` `#` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonarrays and/or jsonobjects
- [int64](#type-int64) `GetInteger[` <"-default" `,` [jsonvalue](#type-jsonvalue) `defaultValue`> `,` `#` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonarrays and/or jsonobjects, with a default value if not found
- [bool](#type-bool) `GetBool[` ... [string](#type-string) `fieldPath` `]`: Gets a value stored within this array, by its index (1-based)
- [bool](#type-bool) `GetBool[` `#` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonarrays and/or jsonobjects
- [bool](#type-bool) `GetBool[` <"-default" `,` [jsonvalue](#type-jsonvalue) `defaultValue`> `,` `#` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonarrays and/or jsonobjects, with a default value if not found
- [string](#type-string) `GetType[` ... [string](#type-string) `fieldPath` `]`: Gets the Type of a value stored within this array, by its index (1-based)
- [uint](#type-uint) `Size`: Allocated capacity of the array
- [uint](#type-uint) `Used`: Total number of values currently in the array
- [string](#type-string) `Type`
- [string](#type-string) `AsString`
- [unistring](#type-unistring) `AsJSON[` <"multiline"> `]`
- [jsonarray](#type-jsonarray) `Value`
- [int64](#type-int64) `SelectKey[` [jsonvalueref](#type-jsonvalueref) `query` `]`
- [int64](#type-int64) `SelectKey[` [jsonobject](#type-jsonobject) `query` `]`
- [jsonarray](#type-jsonarray) `SelectKeys[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [jsonvalue](#type-jsonvalue) `SelectValue[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [jsonarray](#type-jsonarray) `SelectValues[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [jsonarray](#type-jsonarray) `Reverse`: Gives a new jsonarray which re-references json values in reverse order

### Methods
- `GetIterator[` [weakref](#type-weakref) `iteratorObject` `]`: Sets a jsoniterator to iterate this JSON array
- `Clear`: Clears all values from the array
- `Insert[` <"-lazy"> `,` [inr64](#type-inr64) `key` `,` [jsonvalue](#type-jsonvalue) `newValue` `]`
- `Insert[` [int64](#type-int64) `key` `,` [jsonvalue](#type-jsonvalue) `json` `]`: Sets a value within the array, to a new JSON value of any type, e.g. <tt>myJsonArray:Set[1,"{\"subValue\":12}"]</tt>
- `Set[` <"-lazy"> `,` ... [string](#type-string) `fieldPath` `,` [jsonvalue](#type-jsonvalue) `newValue` `]`
- `Set[` [uint](#type-uint) `key` `,` [jsonvalue](#type-jsonvalue) `json` `]`: Sets a value within the array, to a new JSON value of any type, e.g. <tt>myJsonArray:Set[1,"{\"subValue\":12}"]</tt>
- `SetByRef[` [uint](#type-uint) `key` `,` [jsonvalueref](#type-jsonvalueref) `newValue` `]`
- `InsertByRef[` [uint](#type-uint) `key` `,` [jsonvalueref](#type-jsonvalueref) `newValue` `]`
- `AddByRef[` [jsonvalueref](#type-jsonvalueref) `newValue` `]`
- `SetString[` [uint](#type-uint) `key` `,` [string](#type-string) `newValue` `]`: Sets a value within the array, to a new string value
- `SetInteger[` [uint](#type-uint) `key` `,` [int64](#type-int64) `newValue` `]`: Sets a value within the array, to a new integer (int64) value
- `SetNumber[` [uint](#type-uint) `key` `,` [float64](#type-float64) `newValue` `]`: Sets a value within the array, to a new number (float64) value
- `SetBool[` [uint](#type-uint) `key` `,` [bool](#type-bool) `newValue` `]`: Sets a value within the array, to a new boolean value
- `SetNULL[` [uint](#type-uint) `key` `]`: Sets a value within the array, to a null value
- `InsertString[` [uint](#type-uint) `key` `,` [string](#type-string) `newValue` `]`: Inserts a string value within the array
- `InsertInteger[` [uint](#type-uint) `key` `,` [int64](#type-int64) `newValue` `]`: Inserts an integer (int64) value within the array
- `InsertNumber[` [uint](#type-uint) `key` `,` [float64](#type-float64) `newValue` `]`: Inserts a number (float64) value within the array
- `InsertBool[` [uint](#type-uint) `key` `,` [bool](#type-bool) `newValue` `]`: Inserts a boolean value within the array
- `InsertNULL[` [uint](#type-uint) `key` `]`: Inserts a null value within the array
- `Add[` [jsonvalue](#type-jsonvalue) `newValue` `]`: Adds a value to the end of the array, to a new JSON value of any type, e.g. <tt>myJsonArray:Add["{\"subValue\":12}"]</tt>
- `AddString[` [string](#type-string) `newValue` `]`: Adds a string value to the end of the array
- `AddInteger[` [int64](#type-int64) `newValue` `]`: Adds a new integer value to the end of the array
- `AddNumber[` [float64](#type-float64) `newValue` `]`: Adds a new number (float64) value to the end of the array
- `AddBool[` [uint](#type-uint) `key` `,` [bool](#type-bool) `newValue` `]`: Adds a new boolean value to the end of the array
- `AddNULL`: Adds a null value to the end of the array
- `Sort[` <[string](#type-string) `keyProperty`> `]`
- `Erase[` [uint](#type-uint) `key` `]`: Erases the nth value from the array, shifting later items toward 0
- `EraseByQuery[` [string](#type-string) `queryText` `,` <[bool](#type-bool) `removeMatches`=true> `]`: Erases items either matching or not matching the query from the array (depending on the 2nd parameter), shifting later elements toward 0
- `EraseByQuery[` [Query](#type-Query) `ID` `]`: Erases items matching the query from the array, shifting later elements toward 0
- `WriteFile[` [string](#type-string) `filePath` `,` <"multiline"> `,` <[string](#type-string) `lineSplit`="\\r\\n"> `]`
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: For each element in the array, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration (filterQuery: see JSON definition [select](#definition-select))
- `Reverse`
- `Swap[` [int64](#type-int64) `keyA` `,` [int64](#type-int64) `keyB` `]`

### Static Members
- [jsonarray](#type-jsonarray) `New[` <[string](#type-string) `jsonArray`="[]"> `]`



## Type: jsonobject

### Indexers
- [object](#type-object) `jsonobject[` ... [string](#type-string) `fieldPath` `]`

As Text: JSON representation of the object

### Members
- [bool](#type-bool) `Equal[` [jsonvalueref](#type-jsonvalueref) `joOther` `]`
- [bool](#type-bool) `MatchesSchema[` [jsonvalueref](#type-jsonvalueref) `joSchema` `]`
- [jsonobject](#type-jsonobject) `GetMatchingSchema[` [jsonvalueref](#type-jsonvalueref) `joSchema` `]`: Retrieves all matching sub-schemas
- [jsonobject](#type-jsonobject) `Diff[` [jsonvalueref](#type-jsonvalueref) `joNewerObject` `]`: Retrieves an additive changeset between this and a newer version of this object. Additive means items from this object that are not in joNewerObject are ignored. The diff may be merged with the original object to produce a templated joNewerObject.
- [jsonobject](#type-jsonobject) `Duplicate`: Returns a deep copy (completely new and separate clone) of the object
- [object](#type-object) `Get[` ... [string](#type-string) `fieldPath` `]`: Gets a value stored within this object, by its name
- [object](#type-object) `Get[` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonobjects and/or jsonarrays
- [object](#type-object) `Get[` <"-default" `,` [jsonvalue](#type-jsonvalue) `defaultValue`> `,` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonobjects and/or jsonarrays, with a default value if not found
- [jsonvaluecontainer](#type-jsonvaluecontainer) `GetContainer[` ... [string](#type-string) `fieldPath` `]`: Gets a jsonvaluecontainer which holds a value within this object, by its name
- [jsonvaluecontainer](#type-jsonvaluecontainer) `GetContainer[` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a jsonvaluecontainer multiple levels deep within jsonobjects and/or jsonarrays
- [float64](#type-float64) `GetNumber[` ... [string](#type-string) `fieldPath` `]`: Gets a value stored within this object, by its name
- [float64](#type-float64) `GetNumber[` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonobjects and/or jsonarrays
- [float64](#type-float64) `GetNumber[` <"-default" `,` [jsonvalue](#type-jsonvalue) `defaultValue`> `,` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonobjects and/or jsonarrays, with a default value if not found
- [int64](#type-int64) `GetInteger[` ... [string](#type-string) `fieldPath` `]`: Gets a value stored within this object, by its name
- [int64](#type-int64) `GetInteger[` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonobjects and/or jsonarrays
- [int64](#type-int64) `GetInteger[` <"-default" `,` [jsonvalue](#type-jsonvalue) `defaultValue`> `,` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonobjects and/or jsonarrays, with a default value if not found
- [bool](#type-bool) `GetBool[` ... [string](#type-string) `fieldPath` `]`: Gets a value stored within this object, by its name
- [bool](#type-bool) `GetBool[` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonobjects and/or jsonarrays
- [bool](#type-bool) `GetBool[` <"-default" `,` [jsonvalue](#type-jsonvalue) `defaultValue`> `,` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Gets a stored value multiple levels deep within jsonobjects and/or jsonarrays, with a default value if not found
- [string](#type-string) `GetType[` ... [string](#type-string) `fieldPath` `]`: Gets the Type of a value stored within this object, by its name
- [string](#type-string) `Type`
- [string](#type-string) `AsString`
- [unistring](#type-unistring) `AsJSON[` <"multiline"> `]`
- [jsonobject](#type-jsonobject) `Value`
- [bool](#type-bool) `Has[` < ["-notnull"|"-string"|"-array"|"-object"]> `,` ... [string](#type-string) `fieldPath` `]`: Checks whether a value is stored within this object, by its name
- [bool](#type-bool) `Has[` `valueName` `,` `valueName2` `,` ... [string](#type-string) `]`: Checks whether a value is stored, multiple levels deep within jsonobjects and/or jsonarrays
- [bool](#type-bool) `Assert[` <"-lazy"> `,` ... [string](#type-string) `fieldPath` `,` [jsonvalue](#type-jsonvalue) `matchValue` `]`
- [bool](#type-bool) `Assert[` `valueName` `,` `json` `]`: Checks whether a value is stored within this object AND matches the specified JSON value
- [bool](#type-bool) `Assert[` `valueName` `,` `valueName2` `,` ... [string](#type-string) `,` `json` `]`: Checks whether a value is stored, multiple levels deep within jsonobjects and/or jsonarrays, AND matches the specified JSON value
- [jsonarray](#type-jsonarray) `Keys[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: A JSON array containing a list of keys from this object (filterQuery: see JSON definition [select](#definition-select))
- [jsonarray](#type-jsonarray) `Values[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: A JSON array containing a list of values from this object (filterQuery: see JSON definition [select](#definition-select))
- [uint](#type-uint) `Used`: Number of values contained by the object
- [uint](#type-uint) `Size`: Number of values contained by the object
- [unistring](#type-unistring) `SelectKey[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [jsonarray](#type-jsonarray) `SelectKeys[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [jsonvalue](#type-jsonvalue) `SelectValue[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))
- [jsonarray](#type-jsonarray) `SelectValues[` [jsonvalueref](#type-jsonvalueref) `query` `]`: (query: see JSON definition [select](#definition-select))

### Methods
- `GetIterator[` [weakref](#type-weakref) `iteratorObject` `]`: Sets a jsoniterator to iterate this JSON object
- `Clear`: Clears all values from the object
- `Set[` <"-lazy"> `,` ... [string](#type-string) `fieldPath` `,` [jsonvalue](#type-jsonvalue) `newValue` `]`
- `Set[` [string](#type-string) `key` `,` [jsonvalue](#type-jsonvalue) `newValue` `]`: Sets a value within the object, to a new JSON value of any type, e.g. <tt>myJsonObject:Set["someObject","{\"subValue\":12}"]</tt>
- `SetByRef[` [string](#type-string) `key` `,` [jsonvalueref](#type-jsonvalueref) `newValue` `]`
- `SetString[` [string](#type-string) `key` `,` [string](#type-string) `newValue` `]`: Sets a value within the object, to a new string value
- `SetInteger[` [string](#type-string) `key` `,` [int64](#type-int64) `newValue` `]`: Sets a value within the object, to a new integer (int64) value
- `SetNumber[` [string](#type-string) `key` `,` [float64](#type-float64) `newValue` `]`: Sets a value within the object, to a new number (float64) value
- `SetBool[` [string](#type-string) `key` `,` [bool](#type-bool) `newValue` `]`: Sets a value within the object, to a new boolean value
- `SetNULL[` [string](#type-string) `key` `]`: Sets a value within the object, to a null value
- `Erase[` [string](#type-string) `fieldName` `]`: Erases the specified value from the object
- `EraseByQuery[` [string](#type-string) `queryText` `,` <[bool](#type-bool) `removeMatches`=true> `]`: Erases items either matching or not matching the query from the object (depending on the 2nd parameter)
- `EraseByQuery[` [Query](#type-Query) `ID` `]`: Erases items matching the query from the object
- `WriteFile[` [string](#type-string) `filePath` `,` <"multiline"> `,` <[string](#type-string) `lineSplit`="\\r\\n"> `]`
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: For each value in the object, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration (filterQuery: see JSON definition [select](#definition-select))
- `Merge[` [jsonvalueref](#type-jsonvalueref) `jsonObject` `,` <[bool](#type-bool) `replace`=true> `]`

### Static Members
- [jsonobject](#type-jsonobject) `New[` <[string](#type-string) `jsonObject`="{}"> `]`
- [jsonobject](#type-jsonobject) `ParseFile[` [filepath](#type-filepath) `filename` `]`



## Type: lavishmachine
- Static: Yes (All Members/Methods also work as Static Members/Methods)
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- [taskmanager](#type-taskmanager) `NewTaskManager[` `name` `]`: Creates a new, empty, [[LavishScript:Task Manager|Task Manager]], or provides the existing Task Manager by the given name
- [tasktypeset](#type-tasktypeset) `NewTaskTypeSet[` `name` `]`: Creates a new, empty, [[LavishScript:Task Type Set|Task Type Set]]
- [tasktype](#type-tasktype) `NewTaskType[` `json` `]`: Creates a new [[LavishScript:Task Type|Task Type]] from a supplied JSON object
- [tasklibrary](#type-tasklibrary) `NewTaskLibrary[` `name` `]`: Creates a new, empty, [[LavishScript:Task Library|Task Library]], or provides the existing Task Library by the given name
- [taskmanager](#type-taskmanager) `TaskManager[` `#` `]`: Retrieves a Task Manager by ID
- [tasktypeset](#type-tasktypeset) `TaskTypeSet[` `#` `]`: Retrieves a Task Type Set by ID
- [tasktype](#type-tasktype) `TaskType[` `#` `]`: Retrieves a Task Type by ID
- [tasklibrary](#type-tasklibrary) `TaskLibrary[` `#` `]`: Retrieves a Task Library by ID
- [task](#type-task) `Task[` `#` `]`: Retrieves a running Task by ID

### Methods
- `LoadPackageFile[` `filename` `]`: Loads a [[LavishMachine:Package|LavishMachine Package]] from a file containing a JSON object
- `LoadPackageJSON[` `json` `]`: Loads a [[LavishMachine:Package|LavishMachine Package]] from a supplied JSON object
- `LoadTaskTypesFile[` `filename` `]`: Loads [[LavishMachine:Task Types|Task Types]] from a file containing a JSON array
- `LoadTaskTypesJSON[` `json` `]`: Loads [[LavishMachine:Task Types|Task Types]] from a supplied JSON array



## Type: taskpulseargs

### Members
- [task](#type-task) `Task`: The current Task instance to process
- [int64](#type-int64) `Timestamp`: Current Timestamp value, as can be compared to task.StartTimestamp and task.LastFrameTimestamp
- [uint](#type-uint) `ElapsedMS`: Elapsed time, in milliseconds, since the Task started
- [elmactaskstate](#type-elmactaskstate) `TaskState`: One of Start, Continue, or Stop. This indicates the current state of the Task.
- [unistring](#type-unistring) `Error`: The Error, if any, as would be set by taskpulseargs:SetError

### Methods
- `SetError[` `text` `]`: Sets error text associated with the Task



## Type: task

### Members
- [string](#type-string) `Name`: Name of the Task, if one was provided
- [int64](#type-int64) `ID`: ID of the Task
- [tasktype](#type-tasktype) `Type`: Task Type (such as "ls1.echo")
- ??? `TaskManager[`???`]`
- [jsonobject](#type-jsonobject) `Args`: A copy of the object used to initiate the Task, held for the Tasks lifetime. This object can be modified during use to store additional information.
- [jsonvalue](#type-jsonvalue) `Args[` ... [string](#type-string) `]`: Shortcut to retrieve a value from Args, e.g. Task.Args[someObject,someValue] is the same as Task.Args.Get[someObject].Get[someValue] or Task.Args.Get[someObject,someValue]
- [jsonobject](#type-jsonobject) `Result`: The Result object produced by the Task (currently unused)
- [jsonvalue](#type-jsonvalue) `Result[` ... [string](#type-string) `]`: Shortcut to retrieve a value from Result
- [bool](#type-bool) `IsRunning`: TRUE if the Task is currently running.
- [float](#type-float) `RunningTime`: Running Time of the Task, in seconds. NULL if the Task is not running.
- [int64](#type-int64) `RunningTimeMS`: Running Time of the Task, in milliseconds. NULL if the Task is not running.
- [float](#type-float) `FrameElapsed`: Amount of time since the previous Task Frame (Pulse of the Task), in seconds. NULL if the Task is not running.
- [int64](#type-int64) `FrameElapsedMS`: Amount of time since the previous Task Frame (Pulse of the Task), in milliseconds. NULL if the Task is not running.
- [int64](#type-int64) `StartTimestamp`: The timestamp when the Task was started. NULL if the Task is not running.
- [int64](#type-int64) `LastFrameTimestamp`: The timestamp of the previous Task Frame (Pulse of the Task). NULL if the Task is not running.
- [float](#type-float) `Duration`: The defined duration of the Task, in seconds. NULL if the Task does not have a specified duration.
- [int64](#type-int64) `DurationMS`: The defined duration of the Task, in milliseconds. NULL if the Task does not have a specified duration.
- [bool](#type-bool) `IsInstant`: TRUE if the Task is defined as instant

### Methods
- `Start`: Start the Task
- `Stop`: Stop the Task
- `Toggle`: Stop or Start the Task

### Static Members
- [task](#type-task) `Get[` [int64](#type-int64) `id` `]`



## Type: tasktype

### Members
- [string](#type-string) `Name`: Name of the Task Type
- [uint](#type-uint) `ID`: The ID number assigned to the Task Type

### Methods
- `Unregister`: Unregisters the Task Type. The Task Type can no longer be used to begin Tasks



## Type: tasktypeset
- Persistent: No ([weakref](#type-weakref) not supported)

### Members
- ??? `Name[`???`]`
- ??? `ID[`???`]`

### Methods
none.


## Type: tasklibrary

### Members
- [string](#type-string) `Name`: Name of the Task Library
- [int64](#type-int64) `ID`: ID of the Task Library
- ??? `AsJSON[`???`]`
- [jsonvalue](#type-jsonvalue) `Task[` `name` `]`: Retrieve the stored JSON object that defines a Task by a given name. Because a Task Library "is" a JSON object, .Task[name] does the same as .JSON[name]

### Methods
- `Clear`: Clears all Tasks defined in the Task Library
- `Destroy`: Destroys the Task Library, such that it can no longer be found via [[ObjectType:lavishmachine|lavishmachine]].TaskLibrary[name]
- `AddTask[` `name` `,` `jsonobject` `]`: Adds a new Task by name. A Task is defined by a JSON object. Example:   MyTaskLibrary:AddTask[Hello World,"{\"type\":\"ls1.echo\",\"output\":\"Hello World!\"}"]
- `RemoveTask[` `name` `]`: Removes a defined Task by name



## Type: taskmanager

### Members
- [string](#type-string) `Name`: Name of the Task Manager
- [uint](#type-uint) `ID`: The ID number assigned to the Task Manager
- [task](#type-task) `BeginTask[` `jsonobject` `]`: Begins a Task via the provided JSON object, e.g. <tt>TaskManager:BeginTask["{\"type\":\"ls1.echo\",\"output\":\"Hello World!\"}"]</tt>
- [task](#type-task) `BeginTaskLibrary[` `name` `]`: Begins every Task in a given Task Library, wrapped in a parallel Task

### Methods
- `SetTaskTypeSet[`???`]`
- `BeginTask[` `jsonobject` `]`: Begins a Task via the provided JSON object, e.g. <tt>TaskManager:BeginTask["{\"type\":\"ls1.echo\",\"output\":\"Hello World!\"}"]</tt>
- `BeginTaskLibrary[` `name` `]`: Begins every Task in a given Task Library, wrapped in a parallel Task
- `Clear`: Stops all running Tasks
- `Destroy`: Stops all running Tasks, and destroys the Task Manager itself
- `BeginTasksFile[`???`]`
- `BeginTasks[` `jsonarray` `]`: Begins every Task in a given JSON array of Task objects

### Static Members
- [taskmanager](#type-taskmanager) `Default`: The 'default' provided task manager
- [taskmanager](#type-taskmanager) `New[` [string](#type-string) `name` `]`
- [taskmanager](#type-taskmanager) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` [jsonvalueref](#type-jsonvalueref) `filterQuery` `]`: (filterQuery: see JSON definition [select](#definition-select))



## Type: xmlreader

### Initializers
`xmlreader`

As Text: "xmlreader"

### Members
- [string](#type-string) `Error`: The error message, if XML parsing failed
- [xmlnode](#type-xmlnode) `Root`: A root node that contains the actual XML nodes

### Methods
- `AddEntity[` [string](#type-string) `entityName` `,` [string](#type-string) `entityValue` `]`: Adds a custom XML Entity with a specified value
- `Parse[` [string](#type-string) `xml` `]`: Parses XML passed in as a string
- `ParseFile[` [string](#type-string) `filename` `]`: Parses an XML file
- `Reset`: Resets the XML reader to its ready state, removing any previously loaded nodes



## Type: xmlnode

As Text: Same as `Text`

### Members
- [string](#type-string) `Type`: Type of XML node, one of "NONE", "ELEMENT", "COMMENT", "TEXT", "PI". Mostly ELEMENT and TEXT.
- [string](#type-string) `Text`: The text contained by the XML node. For an ELEMENT type, this is the XML tag, e.g. "xyz" from "<xyz>abc</xyz>"; the "abc" would then be a TEXT Child.
- [xmlnode](#type-xmlnode) `Parent`: The parent node in the XML tree
- [xmlnode](#type-xmlnode) `Child`: The first child of this node
- [xmlnode](#type-xmlnode) `LastChild`: The last child of this node
- [xmlnode](#type-xmlnode) `Next`: The next sibling of this node
- [xmlnode](#type-xmlnode) `Previous`: The previous sibling of this node
- ??? `FindChildElement[` [string](#type-string) `name` `]`: Finds the first child ELEMENT node by name (xml tag)
- ??? `FindNextChildElement[` [weakref](#type-weakref) `fromNode` `,` [string](#type-string) `name` `]`: Finds the next child ELEMENT node by name (xml tag), from a specified node
- [bool](#type-bool) `Leaf`
- [jsonarray](#type-jsonarray) `Attributes`: A jsonarray of the attributes and their values
- [jsonobject](#type-jsonobject) `AsJSON[` <[bool](#type-bool) `includeDescendants`=false> `]`: A JSON representation of this element. If includeDescendants is specified, this will include all descendant nodes.

### Methods
- `ForEach[` [string](#type-string) `command` `]`: For each child xmlnode, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration
- `ForEach[` [string](#type-string) `elementName` `,` [string](#type-string) `command` `]`: For each child ELEMENT xmlnode matching the specified elementName (tag), performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration



## Type: autocomplete

### Initializers
`autocomplete`

As Text: "autocomplete"

### Members
- [jsonobject](#type-jsonobject) `Search[` [string](#type-string) `text` `]`
- [jsonobject](#type-jsonobject) `Dictionary`
- [bool](#type-bool) `IsCaseSensitive`
- [bool](#type-bool) `Has[` [string](#type-string) `value` `]`
- [bool](#type-bool) `HasMore[` [string](#type-string) `value` `]`

### Methods
- `SetCaseSensitive[` [bool](#type-bool) `newValue` `]`
- `SetDictionary[` [jsonvalueref](#type-jsonvalueref) `newDictionary` `]`
- `Refresh`




---
# JSON Definitions
## Definition: select
```json
{
  "properties": {
    "member": {
      "type": "string",
      "description": "Name of a Member of the object being tested, to use for all properties (eval, op, with)"
    },
    "args": {
      "type": "array",
      "description": "Optional array of arguments to pass to the specified member"
    },
    "eval": {
      "type": "string",
      "description": "A LavishScript data sequence specifying a different object to test; use Select to refer to the current object (e.g. \"Select.Get[id]\")"
    },
    "op": {
      "type": "string",
      "description": "A test (or series of tests, in the case of && and ||) to perform to determine if the object matches the Select query. The specified op will then require `value`, `list`, or `select`.",
      "enum": [
        "==",
        "!=",
        "<",
        "<=",
        ">",
        ">=",
        "!",
        "&&",
        "||"
      ]
    },
    "with": {
      "type": "array",
      "description": "A list of additional tests, if op succeeds (or is not present)",
      "items": {
        "$ref": "#/definitions/select"
      }
    },
    "limit": {
      "type": "integer",
      "description": "A maximum number of matching results, used for SelectKeys/SelectValues"
    },
    "n": {
      "type": "integer",
      "description": "Used to select the nth matching result, used for SelectKey/SelectValue"
    },
    "value": {
      "description": "A value to test the object against, for the following ops: == != < <= > >="
    },
    "list": {
      "type": "array",
      "description": "A list of additional tests, for the following ops: && ||",
      "items": {
        "$ref": "#/definitions/select"
      }
    },
    "select": {
      "allOf": [
        {
          "$ref": "#/definitions/select"
        }
      ],
      "description": "A specified test, for the following ops: !"
    }
  }
}
```

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
- [lgui2](#type-lgui2) `LGUI2`


---
# Enums
## Type: elgui2anchormode
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `static` = 0
- [int64](#type-int64) `cursor` = 1
- [int64](#type-int64) `element` = 2

## Type: elgui2animationframestate
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `continue` = 1
- [int64](#type-int64) `start` = 0
- [int64](#type-int64) `stop` = -1

## Type: elgui2dpad
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `RELEASED` = -1
- [int64](#type-int64) `N` = 0
- [int64](#type-int64) `NE` = 45
- [int64](#type-int64) `E` = 90
- [int64](#type-int64) `SE` = 135
- [int64](#type-int64) `S` = 180
- [int64](#type-int64) `SW` = 225
- [int64](#type-int64) `W` = 270
- [int64](#type-int64) `NW` = 315

## Type: elgui2edge
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `top` = 0
- [int64](#type-int64) `left` = 1
- [int64](#type-int64) `bottom` = 2
- [int64](#type-int64) `right` = 3

## Type: elgui2fontflags
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `USE_NONE` = 0
- [int64](#type-int64) `USE_FACE` = 1
- [int64](#type-int64) `USE_HEIGHT` = 2
- [int64](#type-int64) `USE_FIXED` = 4
- [int64](#type-int64) `USE_BOLD` = 8
- [int64](#type-int64) `USE_ALL` = `USE_FACE` | `USE_HEIGHT` | `USE_FIXED` | `USE_BOLD`

## Type: elgui2horizontalalignment
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `none` = -1
- [int64](#type-int64) `left` = 0
- [int64](#type-int64) `center` = 1
- [int64](#type-int64) `right` = 2
- [int64](#type-int64) `stretch` = 3

## Type: elgui2imageorientation
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `normal` = 0
- [int64](#type-int64) `mirrorHorizontal` = 1
- [int64](#type-int64) `mirrorVertical` = 2

## Type: elgui2progresstext
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `none` = 0
- [int64](#type-int64) `percent` = 1
- [int64](#type-int64) `value` = 2
- [int64](#type-int64) `valueSlashMax` = 3

## Type: elgui2sizetocontent
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `neither` = 0
- [int64](#type-int64) `width` = 1
- [int64](#type-int64) `height` = 2
- [int64](#type-int64) `both` = 3

## Type: elgui2scrollbar
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `none` = 0
- [int64](#type-int64) `auto` = 1
- [int64](#type-int64) `always` = 2
- [int64](#type-int64) `fit` = 3
- [int64](#type-int64) `fitparent` = 4

## Type: elgui2verticalalignment
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `none` = -1
- [int64](#type-int64) `top` = 0
- [int64](#type-int64) `center` = 1
- [int64](#type-int64) `bottom` = 2
- [int64](#type-int64) `stretch` = 3

## Type: elgui2visibility
- Base Type: [enumvaluetype](#type-enumvaluetype)

Enumeration values/static members:
- [int64](#type-int64) `collapsed` = -1
- [int64](#type-int64) `hidden` = 0
- [int64](#type-int64) `visible` = 1


---
# Types
## Type: lgui2
- Base Type: [lgui2layer](#type-lgui2layer)
- Static: Yes (All Members/Methods also work as Static Members/Methods)

As Text: "LavishGUI 2.0"

### Members
- [lgui2layer](#type-lgui2layer) `Layer`
- [lgui2element](#type-lgui2element) `Element[` [uint](#type-uint) `id` `]`: Retrieves an Element by ID #
- [lgui2element](#type-lgui2element) `Element[` ... [string](#type-string) `locateArgs` `]`
- [...](#type-...) `Element[` `elementName` `,` `elementType` `,` `locateFlags` `]`: [[LGUI2:Locate|Locates]] an Element
- [lgui2elementtype](#type-lgui2elementtype) `ElementType[` [string](#type-string) `name` `]`: Retrieves an Element Type by name
- [lgui2animationtype](#type-lgui2animationtype) `AnimationType[` [string](#type-string) `name` `]`: Retrieves an [[LGUI2:Animation Type|Animation Type]] by name
- [lgui2skin](#type-lgui2skin) `Skin[` <[string](#type-string) `name`> `]`: Retrieves a Skin by name
- [lgui2skin](#type-lgui2skin) `Skin`: The currently active Skin
- [jsonvalue](#type-jsonvalue) `Template[` [string](#type-string) `name` `]`: Retrieves a skinned Template, applying the current Skin stack
- [jsonvalue](#type-jsonvalue) `TemplateValue[` [string](#type-string) `templateName` `,` [string](#type-string) `valueName` `]`: Retrieves a skinned Template value, applying the current Skin stack
- [object](#type-object) `DataBindingContext`: When processing a [[LGUI2:Data Binding|Data Binding]], this is the element or other object that owns the binding
- [object](#type-object) `TriggerContext`: When processing a [[LGUI2:Trigger|Trigger]], this is the element or other object that owns the trigger
- [jsonarray](#type-jsonarray) `Layers`
- [jsonarray](#type-jsonarray) `ElementTypes`
- [jsonarray](#type-jsonarray) `AnimationTypes`
- [jsonarray](#type-jsonarray) `Skins`

### Methods
- `Clear`
- `LoadSkinFile[` [string](#type-string) `filename` `]`
- `PushSkin[` [string](#type-string) `skinName` `]`: Pushes a [[LGUI2:Skin|Skin]] by name onto the Skin stack
- `PopSkin[` [string](#type-string) `skinName` `]`: Pops a [[LGUI2:Skin|Skin]] by name off of the Skin stack, if it is the top of the stack
- `UnloadSkinFile[` [string](#type-string) `filename` `]`
- `RegisterAnimationType[` [jsonobject](#type-jsonobject) `jsonValue` `]`
- `LoadTextElementTypesFile[` [string](#type-string) `filename` `]`
- `LoadTextElementTypesJSON[` [jsonobject](#type-jsonobject) `jsonValue` `]`
- `LoadTextElementTypeJSON[` [jsonobject](#type-jsonobject) `jsonValue` `]`
- `DumpProfiling`



## Type: lgui2eventargs

As Text: "lgui2eventargs"

### Members
- [jsonobject](#type-jsonobject) `Source`: The source of the event being fired.
- [jsonobject](#type-jsonobject) `Args`: Any properties passed with the event
- [jsonvalue](#type-jsonvalue) `Args[` [string](#type-string) `key` `]`: A value from the Args object, by its key
- [bool](#type-bool) `Handled`: TRUE if the event has been acknowledged as handled.
- [jsonobject](#type-jsonobject) `Event`: The event being fired.
- [jsonobject](#type-jsonobject) `Element`: The current element firing the event.
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `SetHandled`: Sets the event "Handled" state to TRUE. This is generally recommended within event handlers. Hooks in particular will ignore the Handled state.



## Type: lgui2animateargs

As Text: "lgui2animateargs"

### Members
- [lgui2element](#type-lgui2element) `Element`: The [[LGUI2:Element|Element]] to animate
- [lgui2animation](#type-lgui2animation) `Animation`: The Animation object
- [jsonobject](#type-jsonobject) `Args`: The Item data (also accessible via Item.Data)
- [jsonvalue](#type-jsonvalue) `Args[` `key` `]`: Retrieves a value from the Item data
- [uint](#type-uint) `Timestamp`: The current Timestamp
- [elgui2animationframestate](#type-elgui2animationframestate) `FrameState`: The current state (Start, Continue, Stop)
- [unistring](#type-unistring) `Error`: An error message set by the SetError method, indicating an error condition on the Animation (and resulting in a Stop)

### Methods
- `SetError[` `error` `]`: An error message to indicate an error condition on a custom Animation. The Animation will Stop.



## Type: lgui2itemviewgeneratorargs


### Members
- [lgui2item](#type-lgui2item) `Item`: The Item to generate a view for
- [unistring](#type-unistring) `ItemType`: The type of Item, either "default" or an explicitly specified value also present in Args
- [jsonobject](#type-jsonobject) `Args`: The Item data (also accessible via Item.Data)
- [jsonvalue](#type-jsonvalue) `Args[` ... [string](#type-string) `fieldPath` `]`: Retrieves a value from the Item data
- [lgui2element](#type-lgui2element) `Parent`: The parent [[LGUI2:Element|Element]] which will contain the Item View (e.g. the ItemsContainer of an [[LGUI2:Item List|Item List]])
- [lgui2element](#type-lgui2element) `View`: The [[LGUI2:Element|Element]] to represent the Item, if it has been set by the Item View Generator
- [unistring](#type-unistring) `Error`: The Error text, if it has been set by the Item View Generator

### Methods
- `SetView[` [jsonobject](#type-jsonobject) `jsonValue` `,` <[weakref](#type-weakref) `context`> `]`: Creates a new [[LGUI2:Element|Element]] (View) to represent the Item
- `SetError[` [string](#type-string) `errorText` `]`: Sets a new Error value



## Type: lgui2canvasrenderer


### Members
- [lgui2fontstyle](#type-lgui2fontstyle) `Font[` [string](#type-string) `name` `]`
- [lgui2brush](#type-lgui2brush) `Brush[` [string](#type-string) `name` `]`
- [float](#type-float) `CanvasHeight`
- [float](#type-float) `CanvasWidth`

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
- [int](#type-int) `Color`: The Color value applied to the brush
- [elgui2imageorientation](#type-elgui2imageorientation) `ImageOrientation`: Transforms to apply to the image
- [string](#type-string) `ImageFilename`: The filename of an image to use for this Brush, if any
- [int](#type-int) `ImageTransparencyKey`: The transparency key value used for the image
- ??? `ImageBrushName[`???`]`
- [jsonvalue](#type-jsonvalue) `PixelShader`: Pixel Shader initialization data, if any
- ??? `VertexShader[`???`]`
- ??? `AsJSON[`???`]`
- ??? `Canvas[`???`]`

### Methods
- `SetColor[` `#aarrggbb` `]`: Sets the new Color value for the brush. e.g. :SetColor["#ffffff"] -- also accepts #rrggbb
- `SetImageOrientation[` [elgui2imageorientation](#type-elgui2imageorientation) `]`
- `SetImage[` `filename` `]`
- `SetImage[` `filename` `,` `colorKey` `]`
- `SetImage[` [weakref](#type-weakref) `binary` `,` [uint](#type-uint) `transparencyColor`=0 `]`
- `SetImageBrushName[`???`]`
- `SetPixelShader[` `json` `]`
- `SetVertexShader[`???`]`
- `SetCanvas[`???`]`



## Type: lgui2animation

As Text: "lgui2animation"

### Members
- [unistring](#type-unistring) `Name`: The name of the Animation
- [lgui2element](#type-lgui2element) `Element`: The Element being animated
- [lgui2animationtype](#type-lgui2animationtype) `Type`: The Animation Type doing the animating
- [jsonobject](#type-jsonobject) `Parameters`: Parameters used to create the Animation. Any changes/additions to this object are kept for the lifetime of the Animation.
- [bool](#type-bool) `IsRunning`: TRUE if the Animation is running
- [float](#type-float) `RunningTime`: Running time (elapsed time) of the Animation, in seconds
- [uint](#type-uint) `RunningTimeMS`: Running time (elapsed time) of the Animation, in milliseconds
- ??? `FrameElapsed[`???`]`
- ??? `FrameElapsedMS[`???`]`
- [uint](#type-uint) `StartTimestamp`: The Animations Start time (milliseconds)
- [uint](#type-uint) `LastFrameTimestamp`: The Animations last frame (milliseconds)
- [float](#type-float) `Duration`: Specified duration (total expected length of time) of the Animation, if any, given in seconds
- [uint](#type-uint) `DurationMS`: Specified duration (total expected length of time) of the Animation, if any, given in milliseconds
- [bool](#type-bool) `IsInstant`: TRUE if the Animation is instant

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
- [string](#type-string) `Face`: Face of the font, such as "Arial"
- [uint](#type-uint) `Height`: Font height, in points
- ??? `HeightFactor[`???`]`
- ??? `HeightOffset[`???`]`
- [bool](#type-bool) `Fixed`: TRUE if the font requests fixed width glyphs
- [bool](#type-bool) `Bold`: TRUE if the font is bold
- [elgui2fontflags](#type-elgui2fontflags) `Flags`: Flags indicating which of the font style properties are explicitly provided, rather than inherited

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
- [lgui2element](#type-lgui2element) `Owner`: The element that owns this Event Handler
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
- [bool](#type-bool) `IsPushNumeric`
- ??? `PullReplaceNULL[`???`]`
- ??? `PullFormat[`???`]`
- ??? `PushFormat[`???`]`
- ??? `PushNULLFormat[`???`]`
- ??? `PullValue[`???`]`
- [jsonobject](#type-jsonobject) `PullRequest`
- ??? `AsJSON[`???`]`

### Methods
- `SetBufferSize[`???`]`
- `SetAutoPull[`???`]`
- `SetAutoPullOnce[`???`]`
- `SetAutoPush[`???`]`
- `SetPullReplaceNULL[`???`]`
- `SetPullFormat[`???`]`
- `SetPushFormat[`???`]`
- `SetPushNumeric[` [bool](#type-bool) `]`
- `SetPushNULLFormat[`???`]`
- `SetPullRequest[` [jsonvalueref](#type-jsonvalueref) `joRequest` `]`
- `PushValue[`???`]`
- `PullValue[`???`]`
- `ApplyStyleJSON[`???`]`



## Type: lgui2inputbinding

As Text: Same as `Name`

### Members
- ??? `Name[`???`]`
- [lgui2eventhandler](#type-lgui2eventhandler) `EventHandler`: The Event Handler that will fire when this Input Binding is activated

### Methods
- `SetName[` `newName` `]`: Changes the name of this Input Binding
- `Remove[`???`]`



## Type: lgui2trigger

As Text: Same as `Name`

### Members
- ??? `Name[`???`]`
- [lgui2eventhandler](#type-lgui2eventhandler) `EventHandler[` `matched|unmatched` `]`: The Event Handler that will fire when this Trigger is either matched or unmatched (depending on the parameter)

### Methods
- `Update`: Updates the Trigger, automatically checking the condition again
- `Update[` [bool](#type-bool) `matched` `]`: Updates the Trigger, manually specifying whether the condition is now matched (TRUE) or unmatched (FALSE)
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
- [lgui2itemlist](#type-lgui2itemlist) `ItemList`: The element hosting this Item
- [unistring](#type-unistring) `Type`: The Item type
- [jsonvalue](#type-jsonvalue) `Data`: The Item data
- [int64](#type-int64) `Index`: The Items index in the ItemList
- [bool](#type-bool) `Selected`: TRUE if the item is selected
- [lgui2element](#type-lgui2element) `View[` `#` `]`: Retrieve an Item view, by the views parent element ID (usually the ItemList.ItemsContainer.ID)
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
- [lgui2radialpanel](#type-lgui2radialpanel) `RadialPanel`: The Radial Panel containing this Radial Item
- [lgui2element](#type-lgui2element) `Element`: The Child of Radial Panel represented by this Radial Item
- [float](#type-float) `ArcLength`: The desired arc length, in degrees, of this Radial Item
- [float](#type-float) `ActualArcLength`: The actual arc length, in degrees, of this Radial Item, after layout
- [float](#type-float) `InnerRadius`: The inner radius (distance from the center of the panel) of this Radial Item
- [float](#type-float) `OuterRadius`: The outer radius (distance from the center of the panel) of this Radial Item. (OuterRadius >= InnerRadius)
- ??? `ZoneMargin[`???`]`
- ??? `LiveZone[`???`]`
- [float](#type-float) `ActualArcLocation`: The actual arc location of this Radial Item, after layout
- [bool](#type-bool) `Contains[` `degreesClockwise` `,` `distance` `]`: TRUE if this Radial Item contains the point at the given vector from the center of the RadialPanel
- [bool](#type-bool) `ContainsPoint[` `#` `,` `#` `]`: TRUE if this Radial Item contains the given X,Y coordinate (relative to the Layer, i.e. the game window)
- [bool](#type-bool) `IsMouseOver`: TRUE if the mouse cursor is over the Radial Item (i.e. ContainsPoint[${Mouse}])
- [float](#type-float) `Opacity`: Opacity value for the Radial Item (usually between 0.0 and 1.0, with 1.0 being 100% opaque and 0.0 being fully transparent)
- [lgui2margins](#type-lgui2margins) `BorderThickness`: Retrieves the thickness of the border
- [lgui2brush](#type-lgui2brush) `BorderBrush`: Retrieves the Brush for the border itself, if applicable
- [lgui2brush](#type-lgui2brush) `BackgroundBrush`: Retrieves the Brush for the background of the area surrounded by the border, if applicable
- [jsonvalue](#type-jsonvalue) `Style[` `name` `]`: Retrieves a [[LGUI2:Style|Style]] by name

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
- [lgui2radialgauge](#type-lgui2radialgauge) `RadialGauge`: The Radial Gauge containing this Radial Gauge Needle
- [unistring](#type-unistring) `Name`: The Name of the needle
- [jsonobject](#type-jsonobject) `JSON`: The needle properties as JSON
- ??? `AsJSON[`???`]`
- [lgui2brush](#type-lgui2brush) `BackgroundBrush`: Retrieves the Brush for the background of the needle
- [float](#type-float) `Origin`: The Origin used for this specific needle, or NULL if not specified (the Radial Gauges origin is used)
- [float](#type-float) `OuterRadius`: The outer radius (distance from the gauges specified center point) for this needle
- [float](#type-float) `InnerRadius`: The inner radius (distance from the gauges specified center point) for this needle
- [float](#type-float) `OuterRadiusFactor`: The outer radius factor for this needle, as a factor of the radial gauges Actual Outer Radius, to be added to OuterRadius
- [float](#type-float) `InnerRadiusFactor`: The inner radius factor for this needle, as a factor of the radial gauges Actual Outer Radius, to be added to InnerRadius
- [float](#type-float) `ActualOuterRadius`: The actual outer radius, as calculated by (OuterRadiusFactor*RadialGauge.ActualOuterRadius)+OuterRadius
- [float](#type-float) `ActualInnerRadius`: The actual inner radius, as calculated by (InnerRadiusFactor*RadialGauge.ActualOuterRadius)+InnerRadius
- [float](#type-float) `InnerArcLength`: The arc length, in degrees, used for the inner edge of the needle
- [float](#type-float) `OuterArcLength`: The arc length, in degrees, used for the outer edge of the needle
- [int](#type-int) `Value`: The current Value for the needle positioning
- [int](#type-int) `MinValue`: The minimum Value for the needle positioning, or NULL if not specified (the Radial Gauges Range is used)
- [int](#type-int) `MaxValue`: The maximum Value for the needle positioning, or NULL if not specified (the Radial Gauges Range is used)
- [uint](#type-uint) `Segments`: Number of segments (2 triangles each) used to render the needle
- [float](#type-float) `MaxValueArcLength`: The arc length used for the needle position when Value>=MaxValue, in degrees clockwise from Origin, or NULL if not specified (the Radial Gauges MaxValueArcLength is used)

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
- [string](#type-string) `Name`: Name of the layer, such as "base" (the default layer)
- [lgui2screen](#type-lgui2screen) `Screen`: The root element for the layer
- [lgui2hud](#type-lgui2hud) `HUD`: Retrieves the HUD element
- [jsonarray](#type-jsonarray) `KeyboardState`
- [lgui2element](#type-lgui2element) `KeyboardFocusElement`: Retrieves the element with keyboard focus, if any
- [lgui2element](#type-lgui2element) `MouseFocusElement`: Retrieves the element with mouse focus, if any
- [lgui2element](#type-lgui2element) `MouseCaptureElement`: Retrieves the element with Mouse Capture, if any
- [float](#type-float) `X`: The X coordinate of the top left corner of this layer
- [float](#type-float) `Y`: The Y coordinate of the top left corner of this layer
- [float](#type-float) `Width`: The Width of this layer
- [float](#type-float) `Height`: The Height of this layer
- [float](#type-float) `CursorX`: The X coordinate of the current mouse cursor position
- [float](#type-float) `CursorY`: The Y coordinate of the current mouse cursor position
- [lgui2element](#type-lgui2element) `ElementFromPoint[` `X` `,` `Y` `]`: Retrieves a UI element, given an (X,Y) pair
- [float](#type-float) `FontScale`: A scaling factor to be applied to font sizes for this layer
- [lgui2element](#type-lgui2element) `LoadFile[` [string](#type-string) `filename` `,` <[weakref](#type-weakref) `context`> `]`: Loads an [[LGUI2:Element|Element]] file into the layer, returning an [[LGUI2:LS1:lgui2element|lgui2element]]-derived object type depending on the LavishGUI 2 element type. A JSON Object is expected in the file.
- [uint](#type-uint) `LoadArrayFile[` [string](#type-string) `filename` `,` <[weakref](#type-weakref) `context`> `]`: Loads a JSON Array file containing [[LGUI2:Element|Elements]] into the layer, returning the number of elements loaded.
- [lgui2element](#type-lgui2element) `LoadReference[` [jsonvalueref](#type-jsonvalueref) `ref` `,` <[weakref](#type-weakref) `context`> `]`: Loads en Element, as defined by a referenced json object, into the layer
- [lgui2element](#type-lgui2element) `LoadJSON[` [jsonobject](#type-jsonobject) `json` `,` <[weakref](#type-weakref) `context`> `]`: Loads an Element, as defined by a json object, into the layer
- [lgui2inputbinding](#type-lgui2inputbinding) `Binding[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `Bindings`
- [jsonobject](#type-jsonobject) `DragDropItem`

### Methods
- `Clear[`???`]`
- `LoadFile[` `filename` `,` <[weakref](#type-weakref) `context`> `]`: Loads an [[LGUI2:Element|Element]] file into the layer. A JSON Object is expected in the file.
- `LoadArrayFile[` `filename` `,` <[weakref](#type-weakref) `context`> `]`: Loads a JSON Array file containing [[LGUI2:Element|Elements]] into the layer.
- `LoadJSON[` `json` `,` <[weakref](#type-weakref) `context`> `]`: Loads an Element, as defined by a json object, into the layer
- `LoadReference[` [jsonvalueref](#type-jsonvalueref) `ref` `,` <[weakref](#type-weakref) `context`> `]`: Loads an Element, as defined by a referenced json object, into the layer
- `LoadPackageFile[` `filename` `,` <[weakref](#type-weakref) `context`> `]`: Loads a [[LGUI2:Package|Package]] from file
- `LoadPackageJSON[` `json` `,` <[weakref](#type-weakref) `context`> `]`: Loads a [[LGUI2:Package|Package]] as defined by a json object
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

### Static Members
- [lgui2layer](#type-lgui2layer) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))



## Type: lgui2skin

As Text: Same as `Name`

### Members
- [string](#type-string) `Name`: Name of the layer, such as "base" (the default layer)
- [jsonvalue](#type-jsonvalue) `Template[` `templateName` `]`: Retrieves a Template from this Skin, by name
- [jsonvalue](#type-jsonvalue) `TemplateValue[` `templateName` `,` `valueKey` `]`: Retrieves a Templated value from this Skin, given the Template name, and Key to the value
- [lgui2font](#type-lgui2font) `Font[` [string](#type-string) `name` `]`
- [lgui2brush](#type-lgui2brush) `Brush[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `Templates`
- [jsonarray](#type-jsonarray) `Brushes`
- [jsonarray](#type-jsonarray) `Fonts`
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `SetTemplate[` `name` `,` `json` `]`: Sets a template within the Skin
- `SetFont[`???`]`
- `SetBrush[`???`]`



## Type: lgui2animationtype

As Text: Same as `Name`

### Members
- [unistring](#type-unistring) `Name`: The name of the Animation Type

### Methods
- `Unregister[`???`]`

### Static Members
- [lgui2animationtype](#type-lgui2animationtype) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))



## Type: lgui2elementtype

As Text: Same as `Name`

### Members
- [string](#type-string) `Name`
- [bool](#type-bool) `IsType[` [string](#type-string) `typeName` `]`: Determines if another LGUI2 element type is, or derives from, this one

### Methods
none.
### Static Members
- [lgui2elementtype](#type-lgui2elementtype) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))



## Type: lgui2element

As Text: "lgui2element"

### Members
- [uint](#type-uint) `ID`: The unique ID number of this element
- [unistring](#type-unistring) `Name`: The specified Name (if any) of this element
- [elgui2visibility](#type-elgui2visibility) `Visibility`
- [lgui2layer](#type-lgui2layer) `Layer`: [[LGUI2:Layer|Layer]] containing the element
- [lgui2elementtype](#type-lgui2elementtype) `ElementType`: The type of Element (e.g. "window")
- [bool](#type-bool) `AcceptsKeyboardFocus`: TRUE if the element accepts keyboard focus, allowing non-mouse input events to route to this element
- [bool](#type-bool) `AcceptsMouseFocus`: TRUE if the element accepts mouse focus
- [jsonobject](#type-jsonobject) `Metadata`: The JSON object (if any) containing any Metadata associated with this element
- [jsonobject](#type-jsonobject) `Metadata[` `TRUE` `]`: The JSON object (automatically created if needed) containing any Metadata associated with this element
- [float](#type-float) `X`: X offset for this element
- [float](#type-float) `Y`: Y offset for this element
- [float](#type-float) `XFactor`: X factor for this element
- [float](#type-float) `YFactor`: Y factor for this element
- [float](#type-float) `Width`: Width for this element (does not include Margins)
- [float](#type-float) `WidthFactor`: Width factor for this element (does not include Margins)
- [float](#type-float) `Height`: Height for this element (does not include Margins)
- [float](#type-float) `HeightFactor`: Height factor for this element (does not include Margins)
- [jsonobject](#type-jsonobject) `StorePlacement`: Retrieves a [[LGUI2:Style|Style]] generated with the elements current placement information, including sizing and positioning
- [elgui2horizontalalignment](#type-elgui2horizontalalignment) `HorizontalAlignment`
- [elgui2verticalalignment](#type-elgui2verticalalignment) `VerticalAlignment`
- [float](#type-float) `ActualX`: Actual X position for this element
- [float](#type-float) `ActualY`: Actual Y position for this element
- [float](#type-float) `ActualWidth`: Actual width of this element (does not include Margins)
- [float](#type-float) `ActualHeight`: Actual height of this element (does not include Margins)
- [float](#type-float) `Strata`: A value essentially indicating the visual "priority" of the element, which affects the order of placement and rendering of the element within its parent. In most cases, this affects element Z-Order. 0.0 is considered the normal "bottom" and 1.0 is considered the normal "top", but the range is not specifically limited.
- [lgui2margins](#type-lgui2margins) `Margins`: Margins surrounding this element (outside its bounds)
- [lgui2margins](#type-lgui2margins) `Padding`: Padding surrounding this elements contents (inside its bounds, and border if applicable)
- [float](#type-float) `Opacity`: Opacity value for the element (usually between 0.0 and 1.0, with 1.0 being 100% opaque and 0.0 being fully transparent)
- [lgui2element](#type-lgui2element) `Locate[` `elementName` `,` `elementType` `,` `flags` `]`: [[LGUI2:Locate|Locates]] an element
- [lgui2fontstyle](#type-lgui2fontstyle) `Font`: The [[LGUI2:Font|Font]] used for this element
- [int](#type-int) `Color`: The foreground color value for this element (for convenience, try using Color.Hex)
- [lgui2element](#type-lgui2element) `ContextMenu`: The [[LGUI2:contextmenu|contextmenu]] (if any) for this element
- [bool](#type-bool) `IsKeyboardFocused`: TRUE if the element is Keyboard Focused (relating to AcceptsKeyboardFocus)
- [bool](#type-bool) `IsMouseFocused`: TRUE if the element is the current Mouse Focus element for the Layer
- [bool](#type-bool) `IsMouseOver`: TRUE if the element is the current MouseOver element for the Layer
- [bool](#type-bool) `IsMouseCaptured`: TRUE if the element has captured mouse input, allowing mouse input events to route to this element regardless of MouseOver state
- [lgui2element](#type-lgui2element) `Parent`: The visual parent, if any, of this element
- [lgui2element](#type-lgui2element) `FirstChild`: The first visual child, if any, of this element
- [lgui2element](#type-lgui2element) `LastChild`: The last visual child, if any, of this element
- [lgui2element](#type-lgui2element) `PreviousSibling`: The previous visual sibling, if any, from this element
- [lgui2element](#type-lgui2element) `NextSibling`: The next visual sibling, if any, from this element
- [jsonarray](#type-jsonarray) `Styles`
- [jsonarray](#type-jsonarray) `Triggers`
- [jsonarray](#type-jsonarray) `Animations`
- [jsonarray](#type-jsonarray) `InputHooks`
- [jsonvalue](#type-jsonvalue) `Style[` `name` `]`: Retrieves a [[LGUI2:Style|Style]] by name
- [lgui2animation](#type-lgui2animation) `Animation[` `name` `]`: Retrieves a loaded [[LGUI2:Animation|Animation]] by name
- [lgui2trigger](#type-lgui2trigger) `Trigger[` `name` `]`: Retrieves a [[LGUI2:Trigger|Trigger]] by name
- ??? `InputHook[`???`]`
- ??? `Tooltip[`???`]`
- [weakref](#type-weakref) `Context[` "self"|"visual"|"logical" `]`
- [lgui2databinding](#type-lgui2databinding) `ContextBinding`

### Methods
- `ForEachChild[` <"true"> `,` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))
- `SetName[` `value` `]`: Assigns a new value to the Name
- `SetVisibility[` [elgui2visibility](#type-elgui2visibility) `]`
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
- `SetHorizontalAlignment[` [elgui2horizontalalignment](#type-elgui2horizontalalignment) `]`
- `SetVerticalAlignment[` [elgui2verticalalignment](#type-elgui2verticalalignment) `]`
- `AddTrigger[` `json` `]`: Adds a [[LGUI2:Trigger|Trigger]] defined by the provided json
- `FireEventHandler[` `name` `]`: Fires a specified Event Handler for the element, with no parameters
- `FireEventHandler[` `name` `,` `json` `]`: Fires a specified Event Handler for the element, passing the given JSON Object
- `FireEventHandler[` `name` `,` `json` `,` [source](#type-source) `element id` `]`: Fires a specified Event Handler for the element, passing the given JSON Object, as from a specified source element
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
- `Animate[` [jsonvalueref](#type-jsonvalueref) `json` `,` [bool](#type-bool) `forceStart`=true `]`: Applies a new [[LGUI2:Animation|Animation]] defined by the provided json
- `SetColor[`???`]`
- `SetFont[`???`]`
- `BubbleToTop`: Bubbles the element to the top of Z-order. This element will be moved over the top of other elements where Strata is less than or equal to its own, and the process will repeat with the elements visual ancestors
- `SetTooltip[`???`]`
- `SetDragDropItem[` [jsonobject](#type-jsonobject) `]`
- `UnsetDragDropItem`
- `SetContext[` [weakref](#type-weakref) `ref` `]`
- `PullContextBinding`

### Static Members
- [lgui2elementtype](#type-lgui2elementtype) `Get[` [int64](#type-int64) `id` `]`
- [lgui2elementtype](#type-lgui2elementtype) `Get[` [string](#type-string) `name` `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: (filterQuery: see JSON definition [select](#definition-select))
- `ForEachGlobal[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: Same as ForEach, but only using elements in the global name table (filterQuery: see JSON definition [select](#definition-select))



## Type: lgui2elementref

### Initializers
- `lgui2elementref[` <[uint](#type-uint) `id`> `]`

As Text: Same as `ID`

### Members
- [uint](#type-uint) `ID`
- [lgui2element](#type-lgui2element) `Element`

### Methods
- `Set[` [uint](#type-uint) `id` `]`



## Type: lgui2anchored
- Base Type: [lgui2element](#type-lgui2element)

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
- Base Type: [lgui2element](#type-lgui2element)

As Text: "lgui2bordered"

### Members
- [lgui2margins](#type-lgui2margins) `BorderThickness`: Retrieves the thickness of the border
- [lgui2brush](#type-lgui2brush) `BorderBrush`: Retrieves the Brush for the border itself, if applicable
- [lgui2brush](#type-lgui2brush) `BackgroundBrush`: Retrieves the Brush for the background of the area surrounded by the border, if applicable

### Methods
- `SetBorderThickness[` `#` `]`: Sets all of this elements BorderThickness values to this #
- `SetBorderThickness[` `#` `,` `#` `]`: Sets Left/Right and Top/Bottom BorderThickness values to these #s (in that order)
- `SetBorderThickness[` `#` `,` `#` `,` `#` `,` `#` `]`: Sets Left, Top, Right, Bottom BorderThickness values to these #s (in that order)
- `SetBorderBrush[` `json` `]`
- `SetBackgroundBrush[` `json` `]`



## Type: lgui2contentbase
- Base Type: [lgui2element](#type-lgui2element)

As Text: "lgui2contentbase"

### Members
- [lgui2element](#type-lgui2element) `Content`: Retrieves the Content stored within the Content Container
- [lgui2element](#type-lgui2element) `ContentContainer`: Retrieves the Content Container used to display the Content

### Methods
- `SetContent[` [jsonvalue](#type-jsonvalue) `json` `,` <[weakref](#type-weakref) `context`> `]`: Sets new Content



## Type: lgui2headeredcontentbase
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2headeredcontentbase"

### Members
- [lgui2element](#type-lgui2element) `Header`: Retrieves the Header stored within the Header Container
- [lgui2element](#type-lgui2element) `HeaderContainer`: Retrieves the Header Container used to display the Content
- [elgui2edge](#type-elgui2edge) `HeaderEdge`: Retrieves the Edge where the Header Container is placed

### Methods
- `SetHeader[` [jsonvalue](#type-jsonvalue) `json` `,` <[weakref](#type-weakref) `context`> `]`: Sets a new Header
- `SetHeaderEdge[` [elgui2edge](#type-elgui2edge) `]`: Sets the Edge where the Header Container is placed



## Type: lgui2itemlist
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2itemlist"

### Members
- [lgui2element](#type-lgui2element) `ItemsContainer`: The element used to contain and display Item views
- [int64](#type-int64) `ItemCount`: The number of Items contained
- [lgui2item](#type-lgui2item) `Item[` `#` `]`: The item at the given position #
- [int64](#type-int64) `SelectedItemCount`: The number of Items selected
- [lgui2item](#type-lgui2item) `SelectedItem`: The first selected item
- [lgui2item](#type-lgui2item) `SelectedItem[` `#` `]`: The nth selected item
- ??? `ItemsBinding[`???`]`
- ??? `SelectedItemBinding[`???`]`
- ??? `SelectedItemBindingProperty[`???`]`
- ??? `ItemByProperty[`???`]`
- ??? `ItemByValue[`???`]`
- [bool](#type-bool) `IsMultiselect`
- [jsonarray](#type-jsonarray) `ItemsSource`

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
- `SetMultiselect[` [bool](#type-bool) `]`
- `SetItemsSource[` [jsonvalueref](#type-jsonvalueref) `jaItemsSource` `]`
- `RefreshItems`



## Type: lgui2anchor
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2anchor"

### Members
- [float](#type-float) `AnchorX`: X-coordinate to anchor to
- [float](#type-float) `AnchorY`: Y-coordinate to anchor to
- [float](#type-float) `AnchorFactorX`: X Factor to anchor to (as a factor to the visual parents size, e.g. 1.0 being the parents full width)
- [float](#type-float) `AnchorFactorY`: Y Factor to anchor to (as a factor to the visual parents size, e.g. 1.0 being the parents full height)
- ??? `AnchorMode[`???`]`
- [bool](#type-bool) `IsClippedToParent`: TRUE if the anchored element is clipped inside the parent (otherwise, it may leave the parent area)
- [float](#type-float) `AnchorOffsetX`: X-coordinate to offset the anchored element by
- [float](#type-float) `AnchorOffsetY`: Y-coordinate to offset the anchored element by
- [float](#type-float) `AnchorOffsetFactorX`: X Factor to offset the anchored element by (as a factor to the anchored elements size, e.g. 0.5 being the anchored elements center)
- [float](#type-float) `AnchorOffsetFactorY`: Y Factor to offset the anchored element by (as a factor to the anchored elements size, e.g. 0.5 being the anchored elements center)

### Methods
- `SetAnchorLocation[` `#` `,` `#` `]`: Sets a new X,Y location to anchor to
- `SetAnchorLocationFactor[` `#` `,` `#` `]`: Sets a new location factor (X,Y) to anchor to
- `SetAnchorOffset[` `#` `,` `#` `]`: Sets a new X,Y offset for the anchored element
- `SetAnchorOffsetFactor[` `#` `,` `#` `]`: Sets a new X,Y offset factor for the anchored element (as a factor to the anchored elements size, e.g. 0.5,0.5 being the anchored elements center)
- `AnchorToCursor`: Enables anchoring to the cursor location, instead of to the AnchorLocation+AnchorLocationFactor
- `SetClipToParent[` `bool` `]`: Sets whether to clip the anchored element inside the parent (if FALSE, it may leave the parent area)



## Type: lgui2border
- Base Type: [lgui2bordered](#type-lgui2bordered)

As Text: "lgui2border"

### Members
- [...](#type-...) `Child`: The one and only Child element contained by the border
- [elgui2horizontalalignment](#type-elgui2horizontalalignment) `HorizontalContentAlignment`: Horizontal alignment to apply to the Child element
- [elgui2verticalalignment](#type-elgui2verticalalignment) `VerticalContentAlignment`: Vertical alignment to apply to the Child element
- ??? `MaintainAspectRatio[`???`]`

### Methods
- `SetChild[` `json` `,` <[weakref](#type-weakref) `context`> `]`
- `SetHorizontalContentAlignment[` [elgui2horizontalalignment](#type-elgui2horizontalalignment) `]`: New horizontal alignment to apply to the Child element
- `SetVerticalContentAlignment[` [elgui2verticalalignment](#type-elgui2verticalalignment) `]`: New vertical alignment to apply to the Child element
- `SetMaintainAspectRatio[`???`]`



## Type: lgui2button
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2button"

### Members
- [bool](#type-bool) `Pressed`: TRUE if the button is currently pressed

### Methods
- `SetPressed[` `TRUE/FALSE` `]`: Sets a new pressed state
- `TogglePressed`: Toggles the pressed state



## Type: lgui2sensitivebutton
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2sensitivebutton"

### Members
- ??? `Value[`???`]`
- ??? `ValueBinding[`???`]`

### Methods
- `SetValue[`???`]`
- `PullValueBinding[`???`]`
- `PushValueBinding[`???`]`



## Type: lgui2knob
- Base Type: [lgui2element](#type-lgui2element)

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
- [lgui2fontstyle](#type-lgui2fontstyle) `Font[` `name` `]`: Retrieves one of the Canvass Fonts, by name
- [lgui2brush](#type-lgui2brush) `Brush[` `name` `]`: Retrieves one of the Canvass Brushes, by name
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
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2checkbox"

### Members
- [bool](#type-bool) `Checked`: TRUE if checked, FALSE if not checked, or NULL if Indeterminate
- ??? `CheckedBinding[`???`]`

### Methods
- `SetChecked[` `newValue` `]`
- `PullCheckedBinding[`???`]`
- `PushCheckedBinding[`???`]`



## Type: lgui2dragger
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2dragger"

### Members
- [bool](#type-bool) `AllowMove`: TRUE if the dragger is allowed to be moved
- [bool](#type-bool) `AllowResize`: TRUE if the dragger is allowed to be resized

### Methods
- `SetAllowMove[` `TRUE/FALSE` `]`: Sets a new AllowMove value
- `SetAllowResize[` `TRUE/FALSE` `]`: Sets a new AllowResize value



## Type: lgui2dragin
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2dragin"

### Members
- [bool](#type-bool) `DraggedIn`: TRUE if a valid item is currently dragged in
- [string](#type-string) `DragDropItemType`: The expected 'dragDropItemType' property, if specified
- [bool](#type-bool) `ValidateItem[` [jsonobject](#type-jsonobject) `item` `]`

### Methods
- `SetDraggedIn[` [bool](#type-bool) `value` `]`: Sets a new DraggedIn value
- `SetDragDropItemType[` [string](#type-string) `value` `]`: Sets a new DragDropItemType value



## Type: lgui2expander
- Base Type: [lgui2headeredcontentbase](#type-lgui2headeredcontentbase)

As Text: "lgui2expander"

### Members
- [bool](#type-bool) `Expanded`: TRUE if the content is expanded

### Methods
- `SetExpanded[` `TRUE/FALSE` `]`: Sets a new Expanded state
- `ToggleExpanded`: Toggles the Expanded state, regardless of the current value



## Type: lgui2filepicker
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2contentbase"

### Members
- [bool](#type-bool) `IsFolderMode`
- [bool](#type-bool) `IsMultiselect`
- [string](#type-string) `Path`
- [string](#type-string) `Filename`
- [string](#type-string) `Wildcard`
- [string](#type-string) `Value`
- [jsonarray](#type-jsonarray) `Values`
- [jsonarray](#type-jsonarray) `FileList`
- [bool](#type-bool) `RequireExisting`
- [bool](#type-bool) `IsAutoRefreshFileList`
- [lgui2databinding](#type-lgui2databinding) `ValueBinding`

### Methods
- `SetFolderMode[` [bool](#type-bool) `]`
- `SetMultiselect[` [bool](#type-bool) `]`
- `SetAutoRefreshFileList[` [bool](#type-bool) `]`
- `SetRequireExisting[` [bool](#type-bool) `]`
- `SetPath[` [string](#type-string) `]`
- `SetFilename[` [string](#type-string) `]`
- `SetWildcard[` [string](#type-string) `]`
- `SetValue[` [string](#type-string) `]`
- `SetValues[` [jsonvalueref](#type-jsonvalueref) `]`
- `SetFileList[` [jsonvalueref](#type-jsonvalueref) `]`
- `RefreshFileList`
- `PullValueBinding`
- `PushValueBinding`



## Type: lgui2imagebox
- Base Type: [lgui2bordered](#type-lgui2bordered)

As Text: "lgui2imagebox"

### Members
- [lgui2brush](#type-lgui2brush) `ImageBrush`: The [[LGUI2:Brush|Brush]] used for the subject of the imagebox
- [bool](#type-bool) `ScaleToFit`: TRUE if the image should be scaled to fit
- [lgui2databinding](#type-lgui2databinding) `ImageBinding`

### Methods
- `SetImageBrush[` `json` `]`: Sets a new [[LGUI2:Brush|Brush]] for the imagebox
- `SetScaleToFit[` `TRUE/FALSE` `]`: Sets a new ScaleToFit value
- `PullImageBinding`



## Type: lgui2inputpicker
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2inputpicker"

### Members
- ??? `Value[`???`]`
- ??? `ValueBinding[`???`]`
- [bool](#type-bool) `IsMultipleControlMode`
- ??? `Summary[`???`]`
- [bool](#type-bool) `IsComboMode`

### Methods
- `SetMultipleControlMode[` [bool](#type-bool) `newValue` `]`
- `SetValue[`???`]`
- `PullValueBinding[`???`]`
- `PushValueBinding[`???`]`
- `SetComboMode[` [bool](#type-bool) `value` `]`



## Type: lgui2ldiopatch
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2ldiopatch"

### Members
- [bool](#type-bool) `BlockLocal`
- [bool](#type-bool) `UseLocalBindings`
- [bool](#type-bool) `UseKeyboard`
- [bool](#type-bool) `UseMouse`
- [bool](#type-bool) `UseOther`

### Methods
- `SetBlockLocal[` [bool](#type-bool) `newValue` `]`
- `SetUseLocalBindings[` [bool](#type-bool) `newValue` `]`
- `SetUseKeyboard[` [bool](#type-bool) `newValue` `]`
- `SetUseMouse[` [bool](#type-bool) `newValue` `]`
- `SetUseOther[` [bool](#type-bool) `newValue` `]`



## Type: lgui2listbox
- Base Type: [lgui2itemlist](#type-lgui2itemlist)

As Text: "lgui2listbox"

### Members
- [bool](#type-bool) `Reorderable`

### Methods
- `SetReorderable[` [bool](#type-bool) `newValue` `]`



## Type: lgui2map
- Base Type: [lgui2itemlist](#type-lgui2itemlist)

As Text: "lgui2map"

### Members
- [bool](#type-bool) `VirtualCenterMode`: TRUE if the view's virtual alignment mode is Center. FALSE if it is Corner (based on Virtual Origin).
- [string](#type-string) `VirtualCenter`: The view's virtual center location, in the form 1.234,5.678
- [float](#type-float) `VirtualCenterX`: The view's virtual center location X-value
- [float](#type-float) `VirtualCenterY`: The view's virtual center location Y-value
- [string](#type-string) `VirtualOrigin`: The view's virtual origin (top left) location, in the form 1.234,5.678
- [float](#type-float) `VirtualLeft`: The view's left-most virtual X-coordinate
- [float](#type-float) `VirtualRight`: The view's right-most virtual X-coordinate
- [float](#type-float) `VirtualTop`: The view's top-most virtual Y-coordinate
- [float](#type-float) `VirtualBottom`: The view's bottom-most virtual Y-coordinate
- [bool](#type-bool) `VirtualScaleMode`: TRUE if the view's virtual size mode is to Scale. FALSE if it is Fixed Size.
- [string](#type-string) `VirtualSize`: The view's virtual size, in the form 1.234,5.678
- [float](#type-float) `VirtualWidth`: The view's virtual width
- [float](#type-float) `VirtualHeight`: The view's virtual height
- [string](#type-string) `VirtualScale`: The view's virtual scale, in the form 1.234,5.678
- [float](#type-float) `VirtualScaleX`: The view's virtual X-scale
- [float](#type-float) `VirtualScaleY`: The view's virtual Y-scale
- [string](#type-string) `ScreenToVirtual[` [float](#type-float) `X` `,` [float](#type-float) `Y` `]`: Transforms a Screen position (e.g. cursor location, ${Mouse}) to a Virtual position in the view; result in the form 1.234,5.678
- [string](#type-string) `VirtualToScreen[` [float](#type-float) `X` `,` [float](#type-float) `Y` `]`: Transforms a Virtual position in the view to a Screen position (e.g. cursor location, ${Mouse}); result in the form 1.234,5.678

### Methods
- `SetVirtualCenter[` [float](#type-float) `X` `,` [float](#type-float) `Y` `]`: Sets the view's Virtual center point, and changes the Virtual Alignment mode to Center
- `SetVirtualOrigin[` [float](#type-float) `X` `,` [float](#type-float) `Y` `]`: Sets the view's Virtual origin (top left) point, and changes the Virtual Alignment mode to Corner
- `SetVirtualSize[` [float](#type-float) `newWidth` `,` [float](#type-float) `newHeight` `]`: Sets the view's Virtual size, and changes the Virtual size mode to Fixed Size
- `SetVirtualSize[` [float](#type-float) `newWidthAndHeight` `]`: Sets the view's Virtual size, and changes the Virtual size mode to Fixed Size
- `SetVirtualScale[` [float](#type-float) `scaleX` `,` [float](#type-float) `scaleY` `]`: Sets the view's Virtual scale, and changes the Virtual size mode to Scale
- `SetVirtualScale[` [float](#type-float) `scaleXandY` `]`: Sets the view's Virtual scale, and changes the Virtual size mode to Scale



## Type: lgui2mapitemview
- Base Type: [lgui2itemview](#type-lgui2itemview)

As Text: "lgui2mapitemview"

### Members
- [bool](#type-bool) `VirtualCenterMode`: TRUE if the item's virtual alignment mode is Center. FALSE if it is Corner (based on Virtual Origin).
- [string](#type-string) `VirtualCenter`: The item's virtual center location, in the form 1.234,5.678
- [float](#type-float) `VirtualCenterX`: The item's virtual center location X-value
- [float](#type-float) `VirtualCenterY`: The item's virtual center location Y-value
- [string](#type-string) `VirtualOrigin`: The item's virtual origin (top left) location, in the form 1.234,5.678
- [float](#type-float) `VirtualLeft`: The item's left-most virtual X-coordinate
- [float](#type-float) `VirtualRight`: The item's right-most virtual X-coordinate
- [float](#type-float) `VirtualTop`: The item's top-most virtual Y-coordinate
- [float](#type-float) `VirtualBottom`: The item's bottom-most virtual Y-coordinate
- [string](#type-string) `VirtualSize`: The item's virtual size, in the form 1.234,5.678
- [float](#type-float) `VirtualWidth`: The item's virtual width
- [float](#type-float) `VirtualHeight`: The item's virtual height

### Methods
- `SetVirtualCenter[` [float](#type-float) `X` `,` [float](#type-float) `Y` `]`: Sets the item's Virtual center point, and changes the Virtual Alignment mode to Center
- `SetVirtualOrigin[` [float](#type-float) `X` `,` [float](#type-float) `Y` `]`: Sets the item's Virtual origin (top left) point, and changes the Virtual Alignment mode to Corner
- `SetVirtualSize[` [float](#type-float) `newWidth` `,` [float](#type-float) `newHeight` `]`: Sets the item's Virtual size
- `SetVirtualSize[` [float](#type-float) `newWidthAndHeight` `]`: Sets the item's Virtual size



## Type: lgui2objectview
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2objectview"

### Members
- ??? `Object[`???`]`
- ??? `Property[`???`]`
- ??? `PropertyNames[`???`]`
- ??? `ObjectBinding`

### Methods
- `ClearProperties[`???`]`
- `AddProperty[`???`]`
- `RemoveProperty[`???`]`
- `PullObjectBinding`



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
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

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
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2itemview"

### Members
- [lgui2itemlist](#type-lgui2itemlist) `ItemList`: The lgui2itemlist containing the Item
- [lgui2item](#type-lgui2item) `Item`: The lgui2item responsible for this view

### Methods
none.


## Type: lgui2autocompletebox
- Base Type: [lgui2textbox](#type-lgui2textbox)

As Text: "lgui2autocompletebox"

### Members
- [jsonobject](#type-jsonobject) `Dictionary`
- [jsonarray](#type-jsonarray) `Suggestions[` <[string](#type-string) `text`> `]`

### Methods
none.


## Type: lgui2combobox
- Base Type: [lgui2listbox](#type-lgui2listbox)

As Text: "lgui2combobox"

### Members
- ??? `Header[`???`]`
- ??? `HeaderContainer[`???`]`
- ??? `HeaderEdge[`???`]`
- [bool](#type-bool) `Open`: TRUE if the combobox drop-down is open

### Methods
- `SetHeaderEdge[`???`]`
- `SetHeader[` [jsonvalue](#type-jsonvalue) `json` `,` <[weakref](#type-weakref) `context`> `]`
- `SetOpen[` `TRUE/FALSE` `]`: Sets a new Open state
- `ToggleOpen`: Toggles the Open state



## Type: lgui2panel
- Base Type: [lgui2bordered](#type-lgui2bordered)

As Text: "lgui2panel"

### Members
- [lgui2element](#type-lgui2element) `AddChild[` [jsonvalue](#type-jsonvalue) `json` `,` <[weakref](#type-weakref) `context`> `]`: Adds a child element to the panel, and returns the element

### Methods
- `AddChild[` [jsonvalue](#type-jsonvalue) `json` `,` <[weakref](#type-weakref) `context`> `]`: Adds a child element to the panel



## Type: lgui2overlay
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

### Members
- [lgui2element](#type-lgui2element) `OverlayContainer`
- [lgui2element](#type-lgui2element) `Overlay`

### Methods
- `SetOverlay[` [jsonvalue](#type-jsonvalue) `json` `,` <[weakref](#type-weakref) `context`> `]`



## Type: lgui2popup
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2popup"

### Members
- [bool](#type-bool) `Open`: Retrieves the current Open state for the popup

### Methods
- `SetOpen[` `TRUE/FALSE` `]`: Sets a new Open state for the popup
- `SetOpen[` `TRUE` `,` `x` `,` `y` `]`: Sets a new Open state for the popup, using the provided (x,y) location if it is TRUE
- `ToggleOpen`: Toggles the Open state for the popup
- `ToggleOpen[` `x` `,` `y` `]`: Toggles the Open state for the popup, using the provided (x,y) location if it is changing to TRUE



## Type: lgui2progressbar
- Base Type: [lgui2bordered](#type-lgui2bordered)

As Text: "lgui2progressbar"

### Members
- [int](#type-int) `Value`: The current value from the progressbar
- [int](#type-int) `MinValue`: The minimum progressbar value
- [int](#type-int) `MaxValue`: The maximum progressbar value
- [lgui2brush](#type-lgui2brush) `FillerBrush`: The [[LGUI2:Brush|Brush]] used for the progress bar filler
- [lgui2brush](#type-lgui2brush) `OverlayBrush`: The [[LGUI2:Brush|Brush]] used for an overlay (usually partly transparent) over the progress bar filler
- [elgui2edge](#type-elgui2edge) `FillFromEdge`: The edge to begin filling from
- [elgui2progresstext](#type-elgui2progresstext) `ProgressText`: The style of progress text, if any, to show on the bar
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
- Base Type: [lgui2bordered](#type-lgui2bordered)

As Text: "lgui2radialgauge"

### Members
- [float](#type-float) `Origin`: Where the radial layout begins, in degrees clockwise from top. 0.0 <= value < 360.0
- [uint](#type-uint) `Resolution`: The number of edges used to render the perimeter of a 360-degree FillerBrush circle. For optimal performance, use the lowest value that still looks good at the desired size
- [float](#type-float) `MaxValueArcLength`: The full arc length, in degrees clockwise from Origin, when Value>=MaxValue -- default is 360.0
- [int](#type-int) `Value`: The current Value for the FillerBrush
- [int](#type-int) `MinValue`: The minimum Value for the FillerBrush Range
- [int](#type-int) `MaxValue`: The maximum Value for the FillerBrush Range
- [lgui2brush](#type-lgui2brush) `FillerBrush`: The [[LGUI2:Brush|Brush]] used to render the Filler arc
- [lgui2brush](#type-lgui2brush) `OverlayBrush`: The [[LGUI2:Brush|Brush]] used to render the Overlay after rendering the Filler and any Needles
- [elgui2progresstext](#type-elgui2progresstext) `ProgressText`: The style of progress text, if any, to show on the bar
- [float](#type-float) `OuterRadius`: The radius from the CenterPoint to the outer edge of the FillerBrush -- default is 0.0
- [float](#type-float) `OuterRadiusFactor`: The radius factor, as a factor of the inner size (excluding padding and border) of the radialgauge, to add to OuterRadius -- default is 0.5
- [float](#type-float) `ActualOuterRadius`: The actual outer radius, as calculated by (OuterRadiusFactor*Size)+OuterRadius, where Size is the smaller between the radial gauges Width and Height
- [float](#type-float) `InnerRadius`: The radius from the CenterPoint to the inner edge of the FillerBrush -- default is 0.0
- [float](#type-float) `InnerRadiusFactor`: The radius factor, as a factor of the inner size (excluding padding and border) of the radialgauge, to add to InnerRadius -- default is 0.0
- [float](#type-float) `ActualInnerRadius`: The actual inner radius, as calculated by (InnerRadiusFactor*Size)+InnerRadius, where Size is the smaller between the radial gauges Width and Height
- [float](#type-float) `CenterPointX`: The X coordinate of the point to use as the center for the FillerBrush and any Needles -- default is 0.0
- [float](#type-float) `CenterPointY`: The Y coordinate of the point to use as the center for the FillerBrush and any Needles -- default is 0.0
- [float](#type-float) `CenterPointXFactor`: The X Factor (as a factor of the actual width of the radialgauge) of the point to use as the center for the FillerBrush and any Needles -- default is 0.5
- [float](#type-float) `CenterPointYFactor`: The Y Factor (as a factor of the actual height of the radialgauge) of the point to use as the center for the FillerBrush and any Needles -- default is 0.5
- [uint](#type-uint) `NeedleCount`: The number of Needles
- [lgui2radialgaugeneedle](#type-lgui2radialgaugeneedle) `Needle[` `#` `]`: The n-th Needle (1-based) if any
- ??? `ValueBinding[`???`]`

### Methods
- `SetOrigin[` `#` `]`: Sets where the radial layout begins, in degrees clockwise from top. This value will automatically adjust into the range 0.0 <= value < 360.0, meaning -1 becomes 359, and 361 becomes 1.
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
- Base Type: [lgiu2panel](#type-lgiu2panel)

As Text: "lgui2radialpanel"

### Members
- [float](#type-float) `DeadZone`: The radius of the Dead Zone in the center of the panel
- [float](#type-float) `LiveZone`: The radius of the Live Zone, the default size for added Radial Items
- [float](#type-float) `ZoneMargin`: The distance between the Dead Zone and Live Zone
- [float](#type-float) `Origin`: Where the radial layout begins, in degrees clockwise from top. 0.0 <= value < 360.0
- [uint](#type-uint) `Resolution`: The number of edges used to render the perimeter of the circle. For optimal performance, use the lowest value that still looks good at the desired size
- [float](#type-float) `ChildWidth`: Width reserved for child elements
- [float](#type-float) `ChildHeight`: Height reserved for child elements
- [lgui2radialitem](#type-lgui2radialitem) `RadialItemByElement[` `#` `]`: Retrieves a [[LGUI2:Radial Item|Radial Item]] from a Child elements ID
- [lgui2radialitem](#type-lgui2radialitem) `RadialItemByVector[` `degreesClockwise` `,` `distance` `]`: Retrieves the [[LGUI2:Radial Item|Radial Item]], if any, at a specified angle and distance from the center
- [lgui2radialitem](#type-lgui2radialitem) `RadialItemByPoint[` `#` `,` `#` `]`: Retrieves the [[LGUI2:Radial Item|Radial Item]], if any, at a specified X,Y location (relative to the Layer, i.e. the game window)
- [lgui2radialitem](#type-lgui2radialitem) `MouseOverItem`: Retrieves the Radial Item that falls under the mouse cursor
- [jsonobject](#type-jsonobject) `RadialItemTemplate`: The base template used for Radial Items added to this panel
- [lgui2brush](#type-lgui2brush) `DeadZoneBrush`: The [[LGUI2:Brush|Brush]] used to render the Dead Zone in the center of the panel

### Methods
- `SetDeadZone[` `#` `]`: Sets the radius of the Dead Zone in the center of the panel
- `SetChildSize[` `#` `]`: Sets the reserved size for child elements to a square of this size
- `SetChildSize[` `#` `,` `#` `]`: Sets the reserved size for child elements to the provided Width and Height
- `SetRadialItemTemplate[` `json` `]`: Sets the base template used for Radial Items added to this panel
- `SetLiveZone[` `#` `]`: Sets the radius of the Live Zone, the default size for added Radial Items
- `SetZoneMargin[` `#` `]`: Sets the distance between the Dead Zone and Live Zone
- `SetOrigin[` `#` `]`: Sets where the radial layout begins, in degrees clockwise from top. This value will automatically adjust into the range 0.0 <= value < 360.0, meaning -1 becomes 359, and 361 becomes 1.
- `SetResolution[` `#` `]`: Sets the number of edges used to render the perimeter of the circle. For optimal performance, use the lowest value that still looks good at the desired size
- `SetDeadZoneBrush[` `json` `]`: Sets the [[LGUI2:Brush|Brush]] used to render the Dead Zone in the center of the panel



## Type: lgui2screen
- Base Type: [lgui2element](#type-lgui2element)

As Text: "lgui2screen"

### Members
none.
### Methods
none.


## Type: lgui2scrollviewer
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2scrollviewer"

### Members
- [float](#type-float) `ViewOffsetX`: The scrolled offset, in pixels, of the views top left corner
- [float](#type-float) `ViewOffsetY`: The scrolled offset, in pixels, of the views top left corner
- [float](#type-float) `MaxViewExtentsWidth`: Maximum scrollable width of the viewed contents, or -1 for automatic
- [float](#type-float) `MaxViewExtentsHeight`: Maximum scrollable height of the viewed contents, or -1 for automatic
- [float](#type-float) `MinViewExtentsWidth`: Minimum scrollable width of the viewed contents
- [float](#type-float) `MinViewExtentsHeight`: Minimum scrollable height of the viewed contents
- [float](#type-float) `ActualViewExtentsWidth`: Actual scrollable width of the viewed contents
- [float](#type-float) `ActualViewExtentsHeight`: Actual scrollable height of the viewed contents
- [elgui2horizontalalignment](#type-elgui2horizontalalignment) `HorizontalContentAlignment`
- [elgui2verticalalignment](#type-elgui2verticalalignment) `VerticalContentAlignment`

### Methods
- `SetViewOffset[` `x` `,` `y` `]`: Sets the scrolled offset, in pixels, of the views top left corner
- `SetMinViewExtents[` `width` `,` `height` `]`: Sets the minimum scrollable extents for the viewed contents
- `SetMaxViewExtents[` `width` `,` `height` `]`: Sets the maximum scrollable extents for the viewed contents
- `SetHorizontalContentAlignment[` [elgui2horizontalalignment](#type-elgui2horizontalalignment) `]`
- `SetVerticalContentAlignment[` [elgui2verticalalignment](#type-elgui2verticalalignment) `]`



## Type: lgui2slider
- Base Type: [lgui2bordered](#type-lgui2bordered)

As Text: "lgui2slider"

### Members
- [int](#type-int) `Value`: The current value from the slider
- [int](#type-int) `MinValue`: The minimum slider value
- [int](#type-int) `MaxValue`: The maximum slider value
- [lgui2element](#type-lgui2element) `Handle`: The sliders handle
- [elgui2edge](#type-elgui2edge) `SlideFromEdge`: The edge the slider begins sliding from
- ??? `ValueBinding[`???`]`

### Methods
- `SetValue[` `#` `]`: Sets a new Value for the slider
- `SetRange[` `#` `,` `#` `]`
- `SetSlideFromEdge[` [elgui2edge](#type-elgui2edge) `]`: Sets the edge the slider begins sliding from
- `PullValueBinding[`???`]`
- `PushValueBinding[`???`]`



## Type: lgui2dockpanel
- Base Type: [lgui2panel](#type-lgui2panel)

As Text: "lgui2dockpanel"

### Members
none.
### Methods
none.


## Type: lgui2hud
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

As Text: "lgui2hud"

### Members
- [lgui2element](#type-lgui2element) `IndicatorIconContainer`
- [lgui2element](#type-lgui2element) `NotificationIconContainer`
- [lgui2item](#type-lgui2item) `DragDropIcon`
- [lgui2element](#type-lgui2element) `TooltipContainer`
- [lgui2element](#type-lgui2element) `TooltipOwner`
- [lgui2item](#type-lgui2item) `AddIndicatorIcon[` `json` `]`
- [lgui2item](#type-lgui2item) `AddNotificationIcon[` `json` `]`

### Methods
- `AddIndicatorIcon[` `json` `]`
- `RemoveIndicatorIcon[`???`]`
- `AddNotificationIcon[` `json` `]`
- `RemoveNotificationIcon[`???`]`
- `SetTooltip[` `element` `,` `x` `,` `y` `,` `json` `]`: Sets the active tooltip
- `UnsetTooltip[` `element` `]`: Un-sets (deactivates) the active tooltip



## Type: lgui2scrollbar
- Base Type: [lgui2dockpanel](#type-lgui2dockpanel)

As Text: "lgui2scrollbar"

### Members
- [int](#type-int) `Value`: The current value from the scrollbar
- [int](#type-int) `MinValue`: The minimum scrollbar value
- [int](#type-int) `MaxValue`: The maximum scrollbar value
- [int](#type-int) `Increment`: Amount to adjust the current value per Mouse Wheel tick
- [int](#type-int) `PageIncrement`: Amount to adjust the current value per Page Up/Down
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
- Base Type: [lgui2panel](#type-lgui2panel)

As Text: "lgui2stackpanel"

### Members
- [bool](#type-bool) `Horizontal`
- [bool](#type-bool) `Uniform`
- ??? `Reversed[`???`]`
- [elgui2horizontalalignment](#type-elgui2horizontalalignment) `HorizontalContentAlignment`
- [elgui2verticalalignment](#type-elgui2verticalalignment) `VerticalContentAlignment`

### Methods
- `SetHorizontal[` `TRUE/FALSE` `]`
- `SetUniform[` `TRUE/FALSE` `]`
- `SetReversed[` `TRUE/FALSE` `]`
- `SetHorizontalContentAlignment[` `newValue` `]`
- `SetVerticalContentAlignment[` `newValue` `]`



## Type: lgui2treepanel
- Base Type: [lgui2stackpanel](#type-lgui2stackpanel)

As Text: "lgui2treepanel"

### Members
none.
### Methods
none.


## Type: lgui2contextmenu
- Base Type: [lgui2itemlist](#type-lgui2itemlist)

As Text: "lgui2contextmenu"

### Members
- [bool](#type-bool) `Open`: TRUE if the Context Menu is currently open

### Methods
- `Open[` `x` `,` `y` `]`: Open the Context Menu at the given (x,y) location
- `Close`: Closes the Context Menu



## Type: lgui2tab
- Base Type: [lgui2headeredcontentbase](#type-lgui2headeredcontentbase)

As Text: "lgui2tab"

### Members
- ??? `IsSelected[`???`]`
- ??? `TabControl[`???`]`

### Methods
- `Select[`???`]`



## Type: lgui2tabcontrol
- Base Type: [lgui2headeredcontentbase](#type-lgui2headeredcontentbase)

As Text: "lgui2tabcontrol"

### Members
- [LS1:lgui2tab](#type-LS1:lgui2tab) `SelectedTab`: The currently selected [[LGUI2:tab|tab]]
- [LS1:lgui2tab](#type-LS1:lgui2tab) `Tab[` `#` `]`: The #th tab
- [int64](#type-int64) `Tabs`: Number of tabs

### Methods
- `SelectTab[` `#` `]`: Selects the #th tab
- `AddTab[` `json` `]`: Adds a tab, given a JSON object defining a [[LGUI2:tab|tab]] element
- `RemoveTab[`???`]`



## Type: lgui2textblock
- Base Type: [lgui2element](#type-lgui2element)

As Text: "lgui2textblock"

### Members
- [string](#type-string) `Text`: The text contained in the textblock
- [bool](#type-bool) `Wrap`: TRUE if the text should be wrapped to additional lines in order to fit
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
- Base Type: [lgui2bordered](#type-lgui2bordered)

As Text: "lgui2textbox"

### Members
- [string](#type-string) `Text`: The text contained in the textbox
- [bool](#type-bool) `Wrap`: TRUE if the text should be wrapped to additional lines in order to fit
- [bool](#type-bool) `Multiline`: TRUE if the textbox allows multiple lines of text
- ??? `TextBinding[`???`]`
- [bool](#type-bool) `TextBindingUsesFocus`

### Methods
- `SetText[` `text` `]`: Sets a new Text value
- `SetWrap[` `bool` `]`: Sets a new Wrap value
- `SetMultiline[` `bool` `]`: Sets a new Multiline value
- `PushTextBinding[`???`]`
- `PullTextBinding[`???`]`
- `SetTextBindingUsesFocus[` [bool](#type-bool) `value` `]`



## Type: lgui2commandbox
- Base Type: [lgui2textbox](#type-lgui2textbox)

As Text: "lgui2commandbox"

### Members
none.
### Methods
none.


## Type: lgui2window
- Base Type: [lgui2headeredcontentbase](#type-lgui2headeredcontentbase)

As Text: "lgui2window"

### Members
- [bool](#type-bool) `Shade`: TRUE if the window is shaded ("minimized" in place but shown as the header)
- [elgui2sizetocontent](#type-elgui2sizetocontent) `SizeToContent`
- [bool](#type-bool) `HideOnClose`: TRUE if the window should Hide instead of Close (and no longer exist), when the Close button is clicked
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
- `SetSizeToContent[` [elgui2sizetocontent](#type-elgui2sizetocontent) `]`
- `SetHideOnClose[` `TRUE/FALSE` `]`: Sets a new HideOnClose state
- `SetAnchorLocation[`???`]`
- `SetAnchorLocationFactor[`???`]`
- `AnchorToCursor[`???`]`
- `SetHeightResizable[`???`]`
- `SetWidthResizable[`???`]`
- `SetAnchorOffset[`???`]`
- `SetAnchorOffsetFactor[`???`]`
- `SetClipToParent[`???`]`
- `SetTitle[` [jsonvalue](#type-jsonvalue) `elementdefinition` `]`



## Type: lgui2wrappanel
- Base Type: [lgui2stackpanel](#type-lgui2stackpanel)

As Text: "lgui2wrappanel"

### Members
- ??? `ChildHeight[`???`]`
- ??? `ChildWidth[`???`]`

### Methods
- `SetChildSize[`???`]`



## Type: lgui2table
- Base Type: [lgui2panel](#type-lgui2panel)

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
- Base Type: [lgui2tab](#type-lgui2tab)

As Text: "lgui2page"

### Members
- ??? `PageControl[`???`]`

### Methods
none.


## Type: lgui2pagecontrol
- Base Type: [lgui2tabcontrol](#type-lgui2tabcontrol)

As Text: "lgui2pagecontrol"

### Members
- ??? `SelectedPage[`???`]`
- ??? `Page[`???`]`
- ??? `Pages[`???`]`

### Methods
- `SelectPage[`???`]`
- `AddPage[`???`]`
- `RemovePage[`???`]`



## Type: lgui2dynamic
- Base Type: [lgui2contentbase](#type-lgui2contentbase)

### Members
- [lgui2databinding](#type-lgui2databinding) `ContentBinding`

### Methods
- `PullContentBinding`




Inner Space Kernel API Specification (LavishScript)

---
# Events
## Event: LavishVM Frame Ends

## Event: OnFrame

## Event: OnMouseEnter

## Event: OnMouseExit

## Event: OnConsoleLine

## Event: OnConsoleLineStripped

## Event: OnCursorPositionUpdated
- Restricted: Yes

## Event: OnCursorStateChanged
- Restricted: Yes

## Event: remoteControlSenderAdded
- Restricted: Yes

## Event: remoteControlSenderRemoved
- Restricted: Yes

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
* `ConsoleRedirect` <[string](#type-string) `LGUIconsoleFQN`> <... [string](#type-string) `command`>

## Command: Exit
### Syntax
* `Exit`

## Command: Wireframe
- Restricted: Yes

### Syntax
* `Wireframe`
* `Wireframe` "on"|"off"|"toggle"

## Command: Gamma
### Syntax
* `Gamma` "-reset"|"-store"|"-display"|"-restore"
* `Gamma` "-inc"|"-dec"|"-set" <[uint](#type-uint) `newLevel`>

## Command: FPS
### Syntax
* `FPS`

## Command: DisplayInfo
### Syntax
* `DisplayInfo`

## Command: GlobalKey
### Syntax
* `GlobalKey` "-keylist"|"-list"
* `GlobalKey` "-clear" [[string](#type-string) `key`]
* `GlobalKey` <[string](#type-string) `key`>

## Command: Bind
- Restricted: Yes

### Syntax
* `Bind` "-keylist"|"-list"|"-clear"
* `Bind` "-delete" <[string](#type-string) `name`>
* `Bind` ["-press"|"-release"] <[string](#type-string) `name`> <[string](#type-string) `keyCombo`> <[string](#type-string) `command`>

## Command: Console
- Restricted: Yes

### Syntax
* `Console` "on"|"off"|"toggle"
* `Console` <[string](#type-string) `LGUIelementFQN`>
* `Console` <[string](#type-string) `sessionOrUplinkName`>

## Command: Press
- Restricted: Yes

### Syntax
* `Press` "-keylist"
* `Press` ["-hold"|"-release"|"-nomodifiers"] <[string](#type-string) `keyCombination`> <[uint](#type-uint) `milliseconds`>

## Command: Type
- Restricted: Yes

### Syntax
* `Type` <[string](#type-string) `text`>

## Command: Services

## Command: Extension
- Restricted: Yes


## Command: GlobalBind
### Syntax
* `GlobalBind` "-list"|"-clear"
* `GlobalBind` "-delete" <[string](#type-string) `name`>
* `GlobalBind` <[string](#type-string) `name`> <[string](#type-string) `keyCombo`> <... [string](#type-string) `command`>

## Command: MouseTo
- Restricted: Yes

### Syntax
* `MouseTo` ["-relative"] <[string](#type-string) `XandY`>

## Command: MouseClick
- Restricted: Yes

### Syntax
* `MouseClick` ["-hold"|"-release"] "left"|"right"

## Command: MouseWheel
- Restricted: Yes

### Syntax
* `MouseWheel` <[int](#type-int) `offset`>

## Command: PlaySound
### Syntax
* `PlaySound` <[string](#type-string) `filename`>
* `PlaySound` "on"|"off"
* `PlaySound` "SystemAsterisk"|"SystemDefault"|"SystemExclamation"|"SystemExit"|"SystemHand"|"SystemQuestion"|"SystemStart"|"SystemWelcome"

## Command: Log
### Syntax
* `Log` <[string](#type-string) `filename`>
* `Log` "off"

## Command: MaxFPS
### Syntax
* `MaxFPS`
* `MaxFPS`
* `MaxFPS`
* `MaxFPS`

## Command: NavPath
- Restricted: Yes


## Command: NavPoint
- Restricted: Yes


## Command: Navigation
- Restricted: Yes


## Command: XMLSetting

## Command: HUDGroup
- Restricted: Yes

### Syntax
* `HUDGroup` <[string](#type-string) `-list`>
* `HUDGroup` "-hide"|"-show"|"-toggle" <[string](#type-string) `name`>

## Command: HUD
- Restricted: Yes

### Syntax
* `HUD` "-list"
* `HUD` "-remove" <[string](#type-string) `name`>
* `HUD` "-add" <[string](#type-string) `name`> <[string](#type-string) `XandY`> <[string](#type-string) `text`>

## Command: HUDSet
- Restricted: Yes

### Syntax
* `HUDSet` <[string](#type-string) `name`> ["-s"] ["-c"] ["-l"] ["-t"]

## Command: HTTPGet
### Syntax
* `HTTPGet` ["-postparam"] ["-postfile"] ["-atom"] ["-file"] <[string](#type-string) `url`>

## Command: Diagnostics
### Syntax
* `Diagnostics`

## Command: Relay
### Syntax
* `Relay` <[string](#type-string) `target`> "-echo" <... [string](#type-string) `message`>
* `Relay` <[string](#type-string) `target`> "-event" <[string](#type-string) `eventName`> [... [string](#type-string) `eventParam`]
* `Relay` <[string](#type-string) `target`> ["-host"] ["-noredirect"] <... [string](#type-string) `command`>

## Command: DotNet
- Restricted: Yes

### Syntax
* `DotNet` "-disableconcurrentgc"
* `DotNet` "-list"
* `DotNet` "-unload" <[string](#type-string) `appDomain`>
* `DotNet` <[string](#type-string) `appDomain`> <[string](#type-string) `assemblyName`> <... [string](#type-string) `appParameters`>

## Command: DotScript
- Restricted: Yes

### Syntax
* `DotScript` "-list"
* `DotScript` "-unload" <[string](#type-string) `appDomain`>
* `DotScript` <[string](#type-string) `xmlFilename`> <... [string](#type-string) `appParameters`>


---
# Top-Level Objects
## TLO: Game

## TLO: Profile

## TLO: Mouse

## TLO: Keyboard

## TLO: Input

## TLO: Display

## TLO: Audio

## TLO: Console
- Restricted: Yes

## TLO: MIDI

## TLO: NavPath
- Restricted: Yes

## TLO: Navigation
- Restricted: Yes

## TLO: Extension
- Restricted: Yes

## TLO: SettingXML

## TLO: InnerSpace
- Restricted: Yes

## TLO: Localization

## TLO: NETObject
- Restricted: Yes

## TLO: LavishSettings

## TLO: DotNet
- Restricted: Yes
- [dotnet](#type-dotnet) `DotNet`


---
# Enums
none.

---
# Types
## Type: innerspace
- Static: Yes (All Members/Methods also work as Static Members/Methods)
- Restricted: Yes

### Members
- [string](#type-string) `Version`: Returns the Inner Space version number
- [string](#type-string) `ISXDK`: Returns the ISXDK version
  - Restricted: Yes
- [int](#type-int) `Build`: Returns the Inner Space build number
- ??? `Stealth[`???`]`
  - Restricted: Yes
- [string](#type-string) `Uplink`: Returns the Name of the current Uplink
- ??? `RemoteControlSenders[`???`]`
  - Restricted: Yes
- [settingsetref](#type-settingsetref) `Configuration`: The main Inner Space settings (InnerSpace.XML)
  - Restricted: Yes
- [settingsetref](#type-settingsetref) `GameConfiguration`: The Inner Space Game Configuration settings (GameConfiguration.XML)
- [settingsetref](#type-settingsetref) `InputConfiguration`: The Inner Space Input Devices configuration settings (InputDevices.XML)
- [agent](#type-agent) `Agent[` `#` `]`: Retrieves an [[ISKernel:Agent|Agent]], by ID
- [jsonarray](#type-jsonarray) `Agents`: Retrieves an array of JSON objects briefly describing all currently defined Agents
- [jsonarray](#type-jsonarray) `AgentProviders`
- [agentprovider](#type-agentprovider) `AgentProvider[` [string](#type-string) `providerName` `]`
- [distributedscope](#type-distributedscope) `AddDistributedScope[` [jsonobject](#type-jsonobject) `json` `]`: Adds a Distributed Scope, given JSON to initialize with
- [distributedscope](#type-distributedscope) `DistributedScope[` [string](#type-string) `name` `]`: Retrieves a Distributed Scope by name
- [jsonarray](#type-jsonarray) `DistributedScopes`: An array of Distributed Scope names
- [bool](#type-bool) `AutoDebug`

### Methods
- `LoadExtension[` [string](#type-string) `name` `]`: Loads <name> extension
  - Restricted: Yes
- `EnableStealth[`???`]`
  - Restricted: Yes
- `ScanAgentsFolder[`???`]`
- `AddAgent[` [jsonobject](#type-jsonobject) `json` `]`: Adds an Agent via a standalone JSON definition
- `FireAgentEvent[`???`]`
- `LoadAgentProviderPackage[` [jsonvalueref](#type-jsonvalueref) `joPackage` `]`
- `AddAgentProvider[` [string](#type-string) `jsonFilename` `]`
- `AddAgentProvider[` [string](#type-string) `jsonFilename` `,` [jsonobject](#type-jsonobject) `json` `]`
- `AddDistributedScope[` [jsonobject](#type-jsonobject) `json` `]`: Adds a Distributed Scope, given JSON to initialize with
- `Relay[` [string](#type-string) `json` `]`
- `Relay[` [string](#type-string) `target` `,` [string](#type-string) `command` `]`
- `Relay[` [string](#type-string) `target` `,` [string](#type-string) `object` `,` [string](#type-string) `method` `,` ... [string](#type-string) `args` `]`
- `RelayByRef[` [jsonvalueref](#type-jsonvalueref) `ref` `]`
- `HostRelay[` [string](#type-string) `json` `]`
- `HostRelay[` [string](#type-string) `target` `,` [string](#type-string) `command` `]`
- `HostRelay[` [string](#type-string) `target` `,` [string](#type-string) `object` `,` [string](#type-string) `method` `,` ... [string](#type-string) `args` `]`
- `HostRelayByRef[` [jsonvalueref](#type-jsonvalueref) `ref` `]`
- `LocalExec[` [string](#type-string) `json` `]`
- `LocalExec[` [string](#type-string) `command` `]`
- `LocalExec[` [string](#type-string) `object` `,` [string](#type-string) `method` `,` ... [string](#type-string) `args` `]`
- `LocalExecByRef[` [jsonvalueref](#type-jsonvalueref) `ref` `]`
- `SetAutoDebug[` [bool](#type-bool) `newValue` `,` <[string](#type-string) `logFilename`> `]`
- `Minidump[` [uint](#type-uint) `processID` `,` <[string](#type-string) `outputFilename`="auto.dmp"> `]`
- `ConnectHost`



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
- Static: Yes (All Members/Methods also work as Static Members/Methods)

As Text: Same as `System`

### Members
- ??? `GetSize[`???`]`
- ??? `TaskbarAutoHide[`???`]`
- [string](#type-string) `System`: Name of the current display system (e.g. Direct3D9)
- [bool](#type-bool) `Windowed`: TRUE if the application is really windowed
- [bool](#type-bool) `AppWindowed`: TRUE if the application thinks it is windowed
- [int](#type-int) `Width`: The games actual resolution width
- [int](#type-int) `Height`: The games actual resolution height
- [int](#type-int) `X`: X position of the full windows left edge
- [int](#type-int) `Y`: Y position of the full windows top edge
- [int](#type-int) `WindowWidth`: Width of the full window
- [int](#type-int) `WindowHeight`: Height of the full window
- [int](#type-int) `Monitors`: Number of monitors
- [monitor](#type-monitor) `Monitor`: Monitor assigned to the application
- [monitor](#type-monitor) `Monitor[` `#` `]`: The #th monitor attached to the system (1-based)
- [int](#type-int) `DesktopX`: X position of the left edge of the windows desktop on the current monitor
- [int](#type-int) `DesktopY`: Y position of the top edge of the windows desktop on the current monitor
- [int](#type-int) `DesktopWidth`: Width of the windows desktop on the current monitor
- [int](#type-int) `DesktopHeight`: Height of the windows desktop on the current monitor
- [int](#type-int) `ViewableX`: X position of the left edge of the windows viewable portion (does not include the border, etc)
- [int](#type-int) `ViewableY`: Y position of the top edge of the windows viewable portion (does not include the border, etc)
- [int](#type-int) `ViewableWidth`: Width of the windows viewable portion
- [int](#type-int) `ViewableHeight`: Height of the windows viewable portion
- [bool](#type-bool) `Foreground`: TRUE if the window is currently the active window on the system
- [rgb](#type-rgb) `GetPixel[` `x` `,` `y` `]`: Retrieves color information of a specific pixel. Coordinates are relative to the viewable portion of the window, not the games actual display mode
  - Restricted: Yes
- [string](#type-string) `PixelSearch`: See [[Inner_Space:Pixel_Search]] for more information.
  - Restricted: Yes
- [int](#type-int) `TextureMem`: Available texture memory, in megabytes
- [float](#type-float) `FPS`: Sustained frames per second (calculated from the last 64 frames)
- [gdiwindow](#type-gdiwindow) `Window`
- [uint](#type-uint) `CurrentMaxFPS`
- [bool](#type-bool) `CurrentMaxFPSCalculate`
- [uint](#type-uint) `ForegroundMaxFPS`
- [bool](#type-bool) `ForegroundMaxFPSCalculate`
- [uint](#type-uint) `BackgroundMaxFPS`
- [bool](#type-bool) `BackgroundMaxFPSCalculate`
- [gdiwindow](#type-gdiwindow) `ForegroundWindow`

### Methods
- `SetTaskbarAutoHide[`???`]`
- `Screencap[`???`]`
- `EnumWindows[`???`]`
- `EnumVisibleWindows[`???`]`
- `SetForegroundMaxFPS[` [uint](#type-uint) `value` `]`
- `SetForegroundMaxFPSCalculate[` [bool](#type-bool) `value` `]`
- `SetBackgroundMaxFPS[` [uint](#type-uint) `value` `]`
- `SetBackgroundMaxFPSCalculate[` [bool](#type-bool) `value` `]`



## Type: monitor

As Text: The monitor's 'name' according to Windows

### Members
- [int](#type-int) `Width`: Width of the monitor in pixels
- [int](#type-int) `Height`: Height of the monitor in pixels
- [int](#type-int) `Left`: Left pixel of the monitor (X coordinate)
- [int](#type-int) `Top`: Top pixel of the monitor (Y coordinate)
- [int](#type-int) `Right`: Right pixel of the monitor (X coordinate)
- [int](#type-int) `Bottom`: Bottom pixel of the monitor (Y coordinate)
- [int](#type-int) `MaximizeWidth`: Width used for maximized windows on this monitor
- [int](#type-int) `MaximizeHeight`: Height used for maximized windows on this monitor
- [int](#type-int) `MaximizeLeft`: Left-most pixel used for maximized windows on this monitor
- [int](#type-int) `MaximizeTop`: Top pixel used for maximized windows on this monitor
- [int](#type-int) `MaximizeRight`: Right-most pixel used for maximized windows on this monitor
- [int](#type-int) `MaximizeBottom`: Bottom pixel used for maximized windows on this monitor
- [bool](#type-bool) `IsPrimary`: TRUE if the monitor is the Primary monitor
- ??? `ID[`???`]`
- [string](#type-string) `Name`: Name of the monitor (e.g. \\.\DISPLAY1 -- you will need to use string.Escape to see the entire thing, or use string.Right[1] to get the monitor number for example)
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
none.
### Static Members
- [monitor](#type-monitor) `Get[` [uint](#type-uint) `id` `]`
- [monitor](#type-monitor) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: audio
- Static: Yes (All Members/Methods also work as Static Members/Methods)

### Members
- [float](#type-float) `VolumeLeft`: (Windows) Current Process left-channel volume level, as per Windows Volume Mixer. 0.0 for silent, 1.0 for full volume.
- [float](#type-float) `VolumeRight`: (Windows) Current Process right-channel volume level, as per Windows Volume Mixer. 0.0 for silent, 1.0 for full volume.
- [float](#type-float) `Volume`: (Windows) Current Process volume level, as per Windows Volume Mixer. 0.0 for silent, 1.0 for full volume.
- [bool](#type-bool) `IsMuted`: (Windows) Current Process Mute setting, as per Windows Volume Mixer
- [audiovoice](#type-audiovoice) `Voice[` `#` `]`: Retrieves an Audio Voice (something that makes sounds) by ID
- [jsonarray](#type-jsonarray) `Voices`: Retrieves a JSON array containing the list of currently available Voices (things that make sounds)
- [audiostream](#type-audiostream) `Stream[` `#` `]`: Retrieves an Audio Stream (a sound) by ID
- [jsonarray](#type-jsonarray) `Streams`: Retrieves a JSON array containing the list of currently available Streams (sounds)
- [float](#type-float) `EngineVolume`: The current Master volume level for Inner Spaces audio engine
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
- [string](#type-string) `Name`: The name of the bind
- [string](#type-string) `Combo`: The key combination used for the bind
- [string](#type-string) `PressCommand`: The command executed when this bind is pressed
- [string](#type-string) `ReleaseCommand`: The command executed when this bind is released
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `SetName[` `name` `]`: Renames the bind
- `SetCombo[` `combo` `]`: Changes the key combination used by the bind
- `SetPressCommand[` `command` `]`: Sets the command executed when this bind is pressed
- `SetReleaseCommand[` `command` `]`: Sets the command executed when this bind is released
- `Press[`???`]`
- `Release[`???`]`
- `Delete`: Deletes the bind

### Static Members
- [bind](#type-bind) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: keyboard
- Static: Yes (All Members/Methods also work as Static Members/Methods)

### Members
- [string](#type-string) `System`: Name of the currently active system for keyboard input (DirectInput, Win32I)
- [ldiopatch](#type-ldiopatch) `InPatch`
- [ldiopatch](#type-ldiopatch) `Listener`
- [ldiopatch](#type-ldiopatch) `BackgroundListener`
- [ldiopatch](#type-ldiopatch) `OutPatch`
  - Restricted: Yes

### Methods
- `Bind[` `name` `,` [key](#type-key) `combination` `,` `command` `]`: Binds a command to a key combination, with a given name (see [[ISSession:Bind (Command)|Bind command]])
- `Bind[` `-press|-release` `,` `name` `,` [key](#type-key) `combination` `,` `command` `]`: Binds a command to a key combination, with a given name (see [[ISSession:Bind (Command)|Bind command]])
- `GetButtonIterator[`???`]`
- `GetAxisIterator[`???`]`
- `GetDpadIterator[`???`]`
- `GetDeviceIterator[`???`]`
- `GetBindIterator[`???`]`
- `DisableBinds[`???`]`
- `EnableBinds[`???`]`
- `SetListener[` [string](#type-string) `ldioPatchName` `]`
- `SetBackgroundListener[` [string](#type-string) `ldioPatchName` `]`
- `SetInPatch[` [string](#type-string) `ldioPatchName` `]`
  - Restricted: Yes



## Type: input
- Static: Yes (All Members/Methods also work as Static Members/Methods)

### Members
- ??? `G15[`???`]`
- ??? `Pending[`???`]`
- [button](#type-button) `Button[` `name` `]`: Retrieves a button object by name
- [axis](#type-axis) `Axis[` `name` `]`: Retrieves an axis object by name
- ??? `Device[`???`]`
- [dpad](#type-dpad) `DPad[` `name` `]`: Retrieves a d-pad object by name
- [bind](#type-bind) `Bind[` `name` `]`: Retrieves the bind with the given name
- [bool](#type-bool) `BindsEnabled`

### Methods
none.


## Type: g15

As Text: "TRUE"

### Members
- [bool](#type-bool) `M1Light`: TRUE if the M1 light is on
- [bool](#type-bool) `M2Light`: TRUE if the M2 light is on
- [bool](#type-bool) `M3Light`: TRUE if the M3 light is on
- [bool](#type-bool) `MRLight`: TRUE if the MR light is on
- [uint](#type-uint) `MLights`: Bit field with M-light states (M1=1,M2=2,M3=4,MR=8)
- [uint](#type-uint) `BacklightLevel`: Keyboard backlight level (0 off, 1 medium, 2 high)
- [uint](#type-uint) `LCDBacklightLevel`: LCD backlight level (0 off, 1 medium, 2 high)

### Methods
- `SetM1Light[` `value` `]`: TRUE for on, FALSE for off
- `SetM2Light[` `value` `]`: TRUE for on, FALSE for off
- `SetM3Light[` `value` `]`: TRUE for on, FALSE for off
- `SetMRLight[` `value` `]`: TRUE for on, FALSE for off
- `SetMLights[` `#` `]`: Set all 4 M-lights with a bit field (M1=1,M2=2,M3=4,MR=8)
- `SetBacklightLevel[` `#` `]`: Set keyboard backlight level (0 off, 1 medium, 2 high)
- `SetLCDBacklightLevel[` `#` `]`: Set LCD backlight level (0 off, 1 medium, 2 high)



## Type: button

As Text: Same as `Name`

### Members
- [string](#type-string) `Name`: Name of the button
- [string](#type-string) `Device`: Name of the input device hosting this button
- [uint](#type-uint) `ID`: ID number of the button -- 255 and under are assigned by Windows, 256 and above are generated by Inner Space for non-keyboard buttons
- [bool](#type-bool) `Pressed`: TRUE if this button is pressed
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `Press`: Presses and releases the button
  - Restricted: Yes
- `Hold`: Presses and holds the button
  - Restricted: Yes
- `Release`: Releases the (pressed) button
  - Restricted: Yes

### Static Members
- [button](#type-button) `Get[` [string](#type-string) `name` `]`
- [button](#type-button) `Get[` "-id" `,` [int](#type-int) `id` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: axis

As Text: Same as `Name`

### Members
- [string](#type-string) `Name`: Name of the axis
- [string](#type-string) `Device`: Name of the input device hosting this axis
- [uint](#type-uint) `ID`: ID number of the axis (independent of buttons or d-pads)
- [float](#type-float) `Position`: Value between 0 and 1 indicating the axis position.  Generally 0 is to the left or downward, and 1 is to the right or upward.  Some axes are a bit more strange, such as Xbox 360 conroller triggers, where the value is the average position of the two triggers -- 0 is left trigger pulled, 1 is right trigger pulled, and 0.5 indicates both triggers are at rest, or both pulled.  The precision of this position is entirely based on the device and its driver (e.g. the values will not just be 0, 0.5, or 1, there might be thousands of possible values).
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `SetPosition[` [float](#type-float) `newValue` `]`

### Static Members
- [axis](#type-axis) `Get[` [string](#type-string) `name` `]`
- [axis](#type-axis) `Get[` "-id" `,` [int](#type-int) `id` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: dpad

As Text: Same as `Name`

### Members
- [string](#type-string) `Name`: Name of the d-pad
- [string](#type-string) `Device`: Name of the input device hosting this d-pad
- [uint](#type-uint) `ID`: ID number of the d-pad (independent of axes or buttons)
- [float](#type-float) `Position`: Value between 0.00 and 360.00 clockwise, indicating the position as a direction.  A value of -1 indicates that the d-pad is at rest (in the middle)
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `SetPosition[` [float](#type-float) `newValue` `]`

### Static Members
- [dpad](#type-dpad) `Get[` [string](#type-string) `name` `]`
- [dpad](#type-dpad) `Get[` "-id" `,` [int](#type-int) `id` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: inputdevice

As Text: Same as `Name`

### Members
- [string](#type-string) `Name`
- ??? `ID[`???`]`
- [string](#type-string) `CurrentKeySet`
- [ldiopatch](#type-ldiopatch) `InPatch`
- [ldiopatch](#type-ldiopatch) `Listener`
- [ldiopatch](#type-ldiopatch) `BackgroundListener`
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `SelectKeySet[`???`]`
- `SetListener[` [string](#type-string) `ldioPatchName` `]`
- `SetBackgroundListener[` [string](#type-string) `ldioPatchName` `]`

### Static Members
- [inputdevice](#type-inputdevice) `Get[` [string](#type-string) `name` `]`
- [inputdevice](#type-inputdevice) `Get[` [int](#type-int) `id` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: joystick

### Members
- [uint](#type-uint) `ID`
- [int](#type-int) `SystemID`
- [uint](#type-uint) `ManufacturerID`
- [uint](#type-uint) `ProductID`
- [jsonobject](#type-jsonobject) `Caps`
- [jsonobject](#type-jsonobject) `AsJSON`
- [bool](#type-bool) `Polling`

### Methods
- `SetPolling[` [bool](#type-bool) `newValue` `]`

### Static Members
- [joystick](#type-joystick) `New[` [jsonvalueref](#type-jsonvalueref) `joystickDefinition` `]`: (joystickDefinition: see JSON definition [joystickDefinition](#definition-joystickDefinition))
- [joystick](#type-joystick) `Get[` [uint](#type-uint) `joystickID` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: mouse
- Static: Yes (All Members/Methods also work as Static Members/Methods)

As Text: Same as `Position`

### Members
- [float](#type-float) `Speed`: Current system mouse speed, 1.0 = 100%
- [int](#type-int) `Threshold1`: Current system mouse acceleration threshold 1
- [int](#type-int) `Threshold2`: Current system mouse acceleration threshold 2
- [int](#type-int) `Acceleration`: Current system mouse acceleration setting
- ??? `DoubleClickTime[`???`]`
- ??? `DoubleClickWidth[`???`]`
- ??? `DoubleClickHeight[`???`]`
- [string](#type-string) `System`: Name of the currently active system for mouse input (DirectInput, Win32I)
- [int](#type-int) `X`: Current mouse X position (horizontal)
- [int](#type-int) `Y`: Current mouse Y position (vertical)
- [string](#type-string) `Position`: Position of the mouse, in the form X,Y, such as 0,0 or 263,475
- ??? `ConvertPosition[`???`]`
- ??? `TranslateX[`???`]`
- ??? `TranslateY[`???`]`
- ??? `ScaleX[`???`]`
- ??? `ScaleY[`???`]`
- [bool](#type-bool) `Cursor`: TRUE if system cursor is visible
- [bool](#type-bool) `BackgroundCursor`: TRUE if Inner Space is rendering the cursor (while the game is inactive)
  - Restricted: Yes
- [ldiopatch](#type-ldiopatch) `InPatch`
- [ldiopatch](#type-ldiopatch) `Listener`
- [ldiopatch](#type-ldiopatch) `BackgroundListener`
- [ldiopatch](#type-ldiopatch) `OutPatch`
  - Restricted: Yes

### Methods
- `LeftClick`: Presses and immediately releases the left mouse button
  - Restricted: Yes
- `RightClick`: Presses and immediately releases the right mouse button
  - Restricted: Yes
- `HoldLeft`: Presses and holds the left mouse button
  - Restricted: Yes
- `ReleaseLeft`: Releases the left mouse button
  - Restricted: Yes
- `HoldRight`: Presses and holds the right mouse button
  - Restricted: Yes
- `ReleaseRight`: Releases the right mouse button
  - Restricted: Yes
- `Wheel[` `#` `]`
  - Restricted: Yes
- `SetPosition[` `x` `,` `y` `]`: Sets the mouse position
  - Restricted: Yes
- `SetBackgroundCursor[` `bool` `]`
  - Restricted: Yes
- `ResetSpeed`: Resets system mouse speed to 100% (Speed=1.0) -- this will cause system lag when applied
- `DisableAcceleration`: Disables system mouse acceleration -- this will cause system lag when applied
- `ShowCursor`
- `HideCursor`
- `SetListener[` [string](#type-string) `ldioPatchName` `]`
- `SetBackgroundListener[` [string](#type-string) `ldioPatchName` `]`
- `SetInPatch[` [string](#type-string) `ldioPatchName` `]`
  - Restricted: Yes



## Type: console
- Static: Yes (All Members/Methods also work as Static Members/Methods)
- Restricted: Yes

### Members
- [bool](#type-bool) `Open`: TRUE if the console is currently visible
- [bool](#type-bool) `Echo`: TRUE if console "echo" is enabled (i.e. not squelched, and echo off has not been used)

### Methods
- `Toggle`: Toggles the console visibility
- `Open`: Opens the console
- `Close`: Closes the console



## Type: extension
- Restricted: Yes

### Members
- [string](#type-string) `Filename`: The extensions filename

### Methods
- `Unload`: Unloads the extension



## Type: navigation
- Static: Yes (All Members/Methods also work as Static Members/Methods)
- Restricted: Yes

### Members
- [navworld](#type-navworld) `World[` `name` `]`: Retrieves the navigation world with this name

### Methods
- `AddWorld[` `name` `]`: Adds the world <name> to the known universe.
- `RemoveWorld[` `name` `]`: Removes the world <name> from the known universe.
- `Export[` `filename` `]`: Exports a given world or universe into <filename>



## Type: navpoint
- Restricted: Yes

As Text: Same as `Name`

### Members
- ??? `ID[`???`]`
- [float](#type-float) `X`: X coordinate
- [float](#type-float) `Y`: Y coordinate
- [float](#type-float) `Z`: Z coordinate
- [string](#type-string) `Name`: Name of the navigational point
- [bool](#type-bool) `ConnectsTo[` `name` `]`: TRUE if the point connects to a specified point
- [bool](#type-bool) `ConnectsFrom[` `name` `]`: TRUE if the point connects from a specified point
- [int](#type-int) `Outgoing`: Number of outgoing connections from this point
- [navpoint](#type-navpoint) `Outgoing[` `n` `]`: nth point with a connection from this point
- [int](#type-int) `Incoming`: Number of incoming connections to this point
- [navpoint](#type-navpoint) `Incoming[` `n` `]`: nth point with a connection to this point
- [string](#type-string) `Custom[` `name` `]`: value of the custom setting <name>
- [string](#type-string) `Note`: A user-defined note set with the navigational point

### Methods
- `SetCustom[` `name` `,` `value` `]`: Sets a Custom data for this point
- `RemoveCustom[` `name` `]`: Removes a Custom data
- `SetPosition[` `#` `,` `#` `,` `#` `]`: Changes the location of the navigational point
- `SetName[` `name` `]`: Changes the name of the nav point
- `SetNote[` `note` `]`: Attaches a note to the navigational point
- `Delete`: Deletes the nav point
- `Rename[` `newname` `]`: Renames a point to <newname>
- `AddConnection[` `name` `]`: Adds a connection to a nav point
- `AddConnection[` `name` `,` `bidirectional` `]`: Adds a bidirectional connection to a nav point
- `RemoveConnection[`???`]`



## Type: navworld
- Restricted: Yes

As Text: Same as `Name`

### Members
- ??? `Name[`???`]`
- [navpoint](#type-navpoint) `Point[` `name` `]`: Retrieves the point with the given name
- [int](#type-int) `Points`: Total number of points in this world
- [int](#type-int) `LastID`: The highest point ID number in this world
- [navpoint](#type-navpoint) `NearestPoint[` `x` `]`: For use in a single coordinate plane system, retrieves the nearest point to (x,0,0)
- [navpoint](#type-navpoint) `NearestPoint[` `x` `,` `y` `]`: Retrieves the nearest point to (x,y,0)
- [navpoint](#type-navpoint) `NearestPoint[` `x` `,` `y` `,` `z` `]`: Retrieves the nearest point to (x,y,z)

### Methods
- `Set[` `name` `,` `x` `]`: For use in a single coordinate plane system, sets a point with the given name at (x,0,0)
- `Set[` `name` `,` `x` `,` `y` `]`: Sets a point with the given name at (x,y,0)
- `Set[` `name` `,` `x` `,` `y` `,` `z` `]`: Sets a point with the given name at (x,y,z)
- `Export[` `filename` `]`: Exports a world to <filename>



## Type: navpath
- Restricted: Yes

### Members
- [int](#type-int) `Points`: The total number of points on this path
- [point3f](#type-point3f) `Point[` `#` `]`: Retrieves a point on the path. (Valid # is 1-Points)
- [string](#type-string) `PointName[` `#` `]`: Retrieves the original name of a point on the path. (Valid # is 1-Points)
- [int](#type-int) `NearestPoint[` `x` `]`: Retrieves the number of the nearest point on the path to location (x,0,0)
- [int](#type-int) `NearestPoint[` `x` `,` `y` `]`: Retrieves the number of the nearest point on the path to location (x,y,0)
- [int](#type-int) `NearestPoint[` `x` `,` `y` `,` `z` `]`: Retrieves the number of the nearest point on the path to location (x,y,z)

### Methods
- `Clear`: Resets the path so it contains no points
- `Reverse`: Reverses the path
- `GetPath[` `world` `,` [point](#type-point) `a` `,` [point](#type-point) `b` `]`: Gets the shortest path from point A to point B (clearing is not required, it is done automatically)
- `GetPath[` `world` `,` [point](#type-point) `a` `,` [point](#type-point) `b` `,` [additional](#type-additional) `points ...` `]`: Gets the shortest path from point A to point B to point C to point D ad infinitum (clearing is not required, it is done automatically)



## Type: ldio
- Static: Yes (All Members/Methods also work as Static Members/Methods)

As Text: "ldio"

### Members
- [jsonarray](#type-jsonarray) `PatchTypes`
- [jsonarray](#type-jsonarray) `Patches`
- [ldiopatch](#type-ldiopatch) `Patch[` [string](#type-string) `patchName` `]`
- [ldiopatch](#type-ldiopatch) `Patch[` [int64](#type-int64) `patchID` `]`

### Methods
- `UnloadPackageFile[` [filepath](#type-filepath) `packageFile` `]`
- `LoadPackage[` [jsonvalueref](#type-jsonvalueref) `joPackage` `]`
- `UnloadPackage[` [jsonvalueref](#type-jsonvalueref) `joPackage` `]`



## Type: midi
- Static: Yes (All Members/Methods also work as Static Members/Methods)

As Text: "midi"

### Members
- [uint](#type-uint) `NumAttachedInDevices`
- ??? `AttachedInDevice[`???`]`
- [jsonarray](#type-jsonarray) `AttachedInDevices`
- [midiindevice](#type-midiindevice) `InDevice[` `#` `]`: A MIDI In Device by its ID number (NOT the same number as Attached devices)
- [uint](#type-uint) `NumInDevices`
- [jsonarray](#type-jsonarray) `InDevices`: A JSON array describing all open MIDI In devices
- [uint](#type-uint) `NumAttachedOutDevices`
- ??? `AttachedOutDevice[`???`]`
- [jsonarray](#type-jsonarray) `AttachedOutDevices`
- ??? `OutDevice[`???`]`
- [uint](#type-uint) `NumOutDevices`
- [jsonarray](#type-jsonarray) `OutDevices`

### Methods
- `OpenAllDevicesIn`: Opens all MIDI In devices, with controls mapped through [[LavishGUI 2]]. The port names will be generated as MIDI 1, MIDI 2, etc
- `CloseAllDevicesIn`: Closes all open MIDI In devices
- `OpenDeviceIn[` `#` `,` `portName` `]`: Opens the #th attached MIDI device (1-based), with controls mapped through [[LavishGUI 2]]. The specified portName is assigned to the device and can be used with the InDevice member
- `OpenDeviceIn[` `#` `,` `portName` `,` `object` `,` `method` `]`: Opens the #th attached MIDI device (1-based), with controls mapped through a [[LavishScript]] object method. The specified portName is assigned to the device and can be used with the InDevice member
- `OpenAllDevicesOut`
- `CloseAllDevicesOut`
- `OpenDeviceOut[`???`]`
- `LoadPackageFile[` [filepath](#type-filepath) `packageFile` `]`



## Type: midiindevice

As Text: "midiindevice"

### Members
- [jsonobject](#type-jsonobject) `AsJSON`: A JSON summary of this device
- [jsonobject](#type-jsonobject) `Metadata`: Metadata associated with this device
- [unistring](#type-unistring) `Name`: The Port Name from this device, as passed to MIDI:OpenDeviceIn
- [unistring](#type-unistring) `DeviceName`: The Name of the device itself, as specified by the device
- [bool](#type-bool) `Retain`
- [bool](#type-bool) `Muted`
- [ldiopatch](#type-ldiopatch) `Output`
- [ldiopatch](#type-ldiopatch) `Feedback`

### Methods
- `Start`: Starts receiving MIDI input, to the receiver specified to MIDI:OpenDeviceIn (either [[LavishGUI 2]] or a LavishScript object method)
- `Stop`: Stops receiving MIDI input
- `Reset`: Resets MIDI input
- `Close`: Closes the midiindevice, which will then be removed from MIDI.InDevices and must be opened again via MIDI:OpenDeviceIn
- `SetRetain[` [bool](#type-bool) `newValue` `]`: Sets whether to keep the device in the background
- `SetMute[` [bool](#type-bool) `newValue` `]`
- `InsertOutput`: Detaches the selected output patch
- `InsertOutput[` [string](#type-string) `name` `]`
- `InsertOutput[` [uint](#type-uint) `id` `]`
- `InsertOutput[` [weakref](#type-weakref) `ldiopatch` `]`
- `SetOutput`: Detaches the selected output patch
- `SetOutput[` [string](#type-string) `name` `]`
- `SetOutput[` [uint](#type-uint) `id` `]`
- `SetOutput[` [weakref](#type-weakref) `ldiopatch` `]`
- `SetFeedback`: Detaches the selected feedback patch
- `SetFeedback[` [string](#type-string) `name` `]`
- `SetFeedback[` [uint](#type-uint) `id` `]`
- `SetFeedback[` [weakref](#type-weakref) `ldiopatch` `]`
- `Simulate[` [string](#type-string) `command` `]`

### Static Members
- [jsonarray](#type-jsonarray) `List`
- [midiindevice](#type-midiindevice) `Get[` [uint](#type-uint) `id` `]`
- [midiindevice](#type-midiindevice) `Get[` [string](#type-string) `name` `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: midioutdevice

As Text: "midioutdevice"

### Members
- [jsonobject](#type-jsonobject) `AsJSON`
- [jsonobject](#type-jsonobject) `Metadata`
- [unistring](#type-unistring) `Name`
- [unistring](#type-unistring) `DeviceName`
- [ldiopatch](#type-ldiopatch) `Patch`

### Methods
- `SendMessage[`???`]`
- `SendJSON[` [jsonvalueref](#type-jsonvalueref) `]`
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

### Static Members
- [jsonarray](#type-jsonarray) `List`
- [midioutdevice](#type-midioutdevice) `Get[` [uint](#type-uint) `id` `]`
- [midioutdevice](#type-midioutdevice) `Get[` [string](#type-string) `name` `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: ldioscene

As Text: "ldioscene"

### Members
- [jsonobject](#type-jsonobject) `AsJSON`
- [unistring](#type-unistring) `Name`
- [bool](#type-bool) `Active`

### Methods
- `Start`
- `Stop`
- `Destroy`

### Static Members
- [ldioscene](#type-ldioscene) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`
- [ldioscene](#type-ldioscene) `New[` [string](#type-string) `sceneName` `,` [jsonvalueref](#type-jsonvalueref) `joldiosceneDefinition` `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: ldiopatch

As Text: "ldiopatch"

### Members
- [int64](#type-int64) `ID`
- [unistring](#type-unistring) `Name`
- [unistring](#type-unistring) `Type`
- [jsonobject](#type-jsonobject) `AsJSON`
- [ldiopatch](#type-ldiopatch) `Output`
- [ldiopatch](#type-ldiopatch) `Listener`
- [bool](#type-bool) `Active`

### Methods
- `ApplyJSON[` [jsonvalueref](#type-jsonvalueref) `joSettings` `]`
- `SetValue`
- `SetValue`
- `SetListener`: Detaches the selected listener patch
- `SetListener[` [string](#type-string) `name` `]`
- `SetListener[` [uint](#type-uint) `id` `]`
- `SetListener[` [weakref](#type-weakref) `ldiopatch` `]`
- `SetOutput`: Detaches the selected output patch
- `SetOutput[` [string](#type-string) `name` `]`
- `SetOutput[` [uint](#type-uint) `id` `]`
- `SetOutput[` [weakref](#type-weakref) `ldiopatch` `]`
- `InsertOutput`: Detaches the selected output patch
- `InsertOutput[` [string](#type-string) `name` `]`
- `InsertOutput[` [uint](#type-uint) `id` `]`
- `InsertOutput[` [weakref](#type-weakref) `ldiopatch` `]`
- `SetActive[` [bool](#type-bool) `newValue` `]`
- `Send[` [string](#type-string) `midiCommandLine` `]`
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
- `SendJSON[` [jsonvalueref](#type-jsonvalueref) `]`

### Static Members
- [ldiopatch](#type-ldiopatch) `Get[` [string](#type-string) `name` `]`
- [ldiopatch](#type-ldiopatch) `Get[` [int64](#type-int64) `patchID` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`
- [ldioscene](#type-ldioscene) `New[` [string](#type-string) `sceneName` `,` [jsonvalueref](#type-jsonvalueref) `joldiosceneDefinition` `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: midiinevent

As Text: "midiinevent"

### Members
- [emidimessage](#type-emidimessage) `Message`: The Windows MIDI message: Open, Close, Data, LongData, Error, LongError
- [uint](#type-uint) `Byte1`: Byte 1 of Data
- [uint](#type-uint) `Byte2`: Byte 2 of Data
- [uint](#type-uint) `Value`: This is a combination of Status, Byte1 and Byte2 (rather, they are derived from this value)
- [uint](#type-uint) `Timestamp`: The MIDI timestamp from the event. This is the length of time since the midiindevice was Started or Reset
- [midiindevice](#type-midiindevice) `Device`: The midiindevice that produced the event
- [uint](#type-uint) `Status`: This is generally a combination of StatusCode and Channel (rather, they are derived from this value)
- [emidistatuscode](#type-emidistatuscode) `StatusCode`: The MIDI Status Code: NoteOff, NoteOn, PolyphonicAftertouch, Control, Program, ChannelAftertouch, Pitch, System
- [uint](#type-uint) `Channel`: For Channel-based Status Codes (all but System), this is the MIDI channel number

### Methods
none.


## Type: webrequest

As Text: "webrequest"

### Members
- [ewebrequeststate](#type-ewebrequeststate) `State`: State of the webrequest, e.g. Idle, Queued, Working, Completed, Aborted
- [ewebrequestas](#type-ewebrequestas) `InterpretAs`: How to interpret the servers response content, such as file, string, json or binary
- [string](#type-string) `URL`: The URL to request
- [jsonarray](#type-jsonarray) `POST`: A JSON array containing a list of objects that describe each POST parameter
- [string](#type-string) `Filename`: The output filename, when interpreting as file
- [jsonobject](#type-jsonobject) `Result`: A JSON object containing response codes and data received as a result of the request
- [binary](#type-binary) `Binary`: A binary object containing the servers response content
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `FromJSON[` `json` `]`: Initializes the webrequest via a JSON object. The webrequest must be in its Idle (Reset) state
- `Reset`: Resets the webrequest to its original Idle state, clearing any settings. The webrequest must not be in Working state. If in Queued state, this will act as :Abort instead
- `SetURL[` `url` `]`: Sets the URL to use. The webrequest must be in Idle or Queued state to change the URL.
- `InterpretAs[` `as` `]`: Tells the webrequest to provide the result as one of <tt>string</tt>, <tt>json</tt>, <tt>binary</tt>
- `InterpretAs[` `file` `,` [absolute](#type-absolute) `filename` `]`: Tells the webrequest to provide the result as a file, to the specified absolute filename (it is recommended to include the full path)
- `Begin`: Begins the webrequest. The webrequest must be in Idle state, and a URL must be set
- `Abort`: Aborts the webrequest. The webrequest must be in Queued state; an aborted webrequest will change to Aborted state when it otherwise would have changed to Working state.



## Type: agent

As Text: "agent"

### Members
- [uint](#type-uint) `ID`: The Agents ID number, assigned when the Agent is loaded
- [unistring](#type-unistring) `Name`: The Name of the Agent
- [bool](#type-bool) `Started`: TRUE if the Agent is Started
- ??? `AutoStart[`???`]`
- [jsonobject](#type-jsonobject) `Metadata`: Metadata associated with the Agent
- ??? `Args[`???`]`
- [filepath](#type-filepath) `Directory`: If the Agent is in its own directory, this is that directory
- ??? `Version[`???`]`
- ??? `Description[`???`]`
- ??? `LGUI2MainElementName[`???`]`
- ??? `LGUI2MainElement[`???`]`
- ??? `MinimumBuild[`???`]`
- ??? `Provides[`???`]`
- ??? `Conflicts[`???`]`
- ??? `Dependencies[`???`]`
- [anonevent](#type-anonevent) `OnAgentEvent`
- [anonevent](#type-anonevent) `OnPulse`
- [anonevent](#type-anonevent) `OnShutdown`
- [anonevent](#type-anonevent) `OnStartup`
- [anonevent](#type-anonevent) `OnPlatformPreStartup`
- [anonevent](#type-anonevent) `OnPlatformStartup`
- [anonevent](#type-anonevent) `OnReload`

### Methods
- `Start`: Starts the Agent. Event handlers will start firing
- `Stop`: Stops the Agent. Event handlers will stop firing
- `Reload`
- `Remove`: Stops and Removes the Agent
- `Uninstall`: Uninstalls the Agent
- `SetAutoStart[`???`]`
- `SetEventHandler[` [string](#type-string) `type` `,` [string](#type-string) `json` `]`: Where <tt>type</tt> is one of "global" "platform" or "process", this sets a specified event handler to the given json
- `FireEvent[` [string](#type-string) `name` `]`: Fires the event by the specified name. Event handlers are processed in the following order: global, platform, process
- `FireEvent[` "-reverse" `,` [string](#type-string) `name` `]`: Fires the event by the specified name, in reverse order. This is used, for example, for "onAgentShutdown" to initiate the process shutdown, then platform shutdown, then global shutdown handlers

### Static Members
- [agent](#type-agent) `New[` [string](#type-string) `json` `]`
- [agent](#type-agent) `Get[` [string](#type-string) `name` `]`
- [agent](#type-agent) `Get[` [uint](#type-uint) `id` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`
- [anonevent](#type-anonevent) `OnAgentAdded`
- [anonevent](#type-anonevent) `OnAgentRemoved`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: sequenceedit
- Restricted: Yes


### Members
none.
### Methods
- `SetSequence[`???`]`
- `New[`???`]`
- `Remove[`???`]`



## Type: gdiwindow

### Initializers
- `gdiwindow[` [string](#type-string) `hexHWND` `]`

As Text: hex HWND

### Members
- ??? `ProcessID[`???`]`
- ??? `ProcessName[`???`]`
- [???](#type-???) `IsForeground`
- [???](#type-???) `Monitor`
- [???](#type-???) `HWND`
- ??? `IsMaximized[`???`]`
- ??? `IsVisible[`???`]`
- ??? `IsMouseOver[`???`]`
- [???](#type-???) `Width`
- [???](#type-???) `Height`
- [???](#type-???) `X`
- [???](#type-???) `Y`
- [???](#type-???) `ViewableX`
- [???](#type-???) `ViewableY`
- [???](#type-???) `ViewableWidth`
- [???](#type-???) `ViewableHeight`
- ??? `MenuWidth[`???`]`
- ??? `MenuHight[`???`]`
- ??? `Text[`???`]`
- [???](#type-???) `AlwaysOnTop`
- [???](#type-???) `Frame`
- ??? `Style[`???`]`
- [bool](#type-bool) `Valid`

### Methods
- `Set[`???`]`
- `SetTaskbarTabVisible[`???`]`
- `MouseMove[`???`]`
  - Restricted: Yes
- `MouseWheel[`???`]`
  - Restricted: Yes
- `Click[`???`]`
  - Restricted: Yes
- `Press[`???`]`
  - Restricted: Yes
- `SendMessage[`???`]`
  - Restricted: Yes
- `PostMessage[`???`]`
  - Restricted: Yes
- `Paste[`???`]`
  - Restricted: Yes
- `SetMenu[`???`]`
  - Restricted: Yes
- `SelectMenuItem[`???`]`
  - Restricted: Yes
- `Flash`: Causes window frame to flash
- `SetText`: Set window title
- `SetForegroundWindow`



## Type: localization
- Static: Yes (All Members/Methods also work as Static Members/Methods)

As Text: Same as `Language`

### Members
- [string](#type-string) `Language`: Name of the current language
- [string](#type-string) `GetString[` `category` `,` `name` `]`: Retrieves a localized string with the given name, in the given category, if both exist
- [string](#type-string) `GetString[` `category` `,` `name` `,` `default` `]`: Same as above, but will create the category and name if they do not exist, and the string will be populated with the default
- [bool](#type-bool) `HasCategory[` `name` `]`: TRUE if a category with the given name exists in the current localization set

### Methods
- `SetString[` `category` `,` `name` `,` `value` `]`: Sets a localized string with the given name in the given category, creating both if necessary
- `RemoveString[` `category` `,` `name` `]`: Removes a localized string with the given name from the given category
- `RemoveCategory[` `category` `]`: Removes a given category (and any settings in it)
- `ExportLanguage[` [string](#type-string) `languageName` `]`: Stores the current localization set (all categories and strings) as the given language (e.g. give a language name, not a filename)
- `ImportLanguage[` [string](#type-string) `languageName` `]`: Imports a language into the current localization set, replacing any existing strings with those in the new language



## Type: lgui2videofeedsource
- Base Type: [lgui2element](#type-lgui2element)

As Text: "lgui2videofeedsource"

### Members
- [string](#type-string) `FeedName`
- [videofeed](#type-videofeed) `Feed`

### Methods
- `SetFeedName`



## Type: lgui2remotecontrol
- Base Type: [lgui2element](#type-lgui2element)

As Text: "lgui2remotecontrol"

### Members
- [bool](#type-bool) `KeyboardEnabled`
  - Restricted: Yes
- [bool](#type-bool) `MouseEnabled`
  - Restricted: Yes
- [bool](#type-bool) `MouseFeedbackEnabled`
  - Restricted: Yes
- [bool](#type-bool) `UseLocalBindings`
  - Restricted: Yes
- [bool](#type-bool) `SendForegroundOnly`
  - Restricted: Yes
- ??? `Clones[`???`]`
  - Restricted: Yes
- [bool](#type-bool) `OffsetByChildWindow`
  - Restricted: Yes
- [bool](#type-bool) `AutoOffsetByChildWindow`
  - Restricted: Yes

### Methods
- `SetKeyboardEnabled[` [bool](#type-bool) `newValue` `]`
  - Restricted: Yes
- `SetMouseEnabled[` [bool](#type-bool) `newValue` `]`
  - Restricted: Yes
- `SetMouseFeedbackEnabled[` [bool](#type-bool) `newValue` `]`
  - Restricted: Yes
- `SetUseLocalBindings[` [bool](#type-bool) `newValue` `]`
  - Restricted: Yes
- `SetSendForegroundOnly[` [bool](#type-bool) `newValue` `]`
  - Restricted: Yes
- `SetOffsetByChildWindow[` [bool](#type-bool) `newValue` `]`
  - Restricted: Yes
- `SetAutoOffsetByChildWindow[` [bool](#type-bool) `newValue` `]`
  - Restricted: Yes
- `AddClone[` [string](#type-string) `]`
  - Restricted: Yes
- `RemoveClone[` [string](#type-string) `]`
  - Restricted: Yes
- `ClearClones`
  - Restricted: Yes

### Static Members
- [jsonarray](#type-jsonarray) `Senders`
- [bool](#type-bool) `RemoteControlAllowed`

### Static Methods
- `SetRemoteControlAllowed[` [bool](#type-bool) `newValue` `]`



## Type: lgui2videofeed
- Base Type: [lgui2remotecontrol](#type-lgui2remotecontrol)

As Text: "lgui2videofeed"

### Members
- ??? `FeedName[`???`]`
- ??? `Feed[`???`]`
- ??? `Permanent[`???`]`
- ??? `FeedNameBinding[`???`]`

### Methods
- `SetFeedName[`???`]`
- `SetPermanent[`???`]`
- `PullFeedNameBinding[`???`]`
- `PushFeedNameBinding[`???`]`



## Type: lgui2broadcaster
- Base Type: [lgui2remoteonctrol](#type-lgui2remoteonctrol)

As Text: "lgui2broadcaster"

### Members
- ??? `BroadcastTarget[`???`]`
  - Restricted: Yes
- ??? `BlockLocal[`???`]`
  - Restricted: Yes
- ??? `Receiver[`???`]`
  - Restricted: Yes

### Methods
- `SetBroadcastTarget[`???`]`
  - Restricted: Yes
- `SetBlockLocal[`???`]`
  - Restricted: Yes
- `SetReceiver[`???`]`
  - Restricted: Yes



## Type: lavishsettings
- Base Type: [settingset](#type-settingset)

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
- Base Type: [settingnode](#type-settingnode)

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
- Base Type: [settingnode](#type-settingnode)

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
- Base Type: [settingnode](#type-settingnode)

### Indexers
- [string](#type-string) `settingset`

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
- `ImportINI[` [string](#type-string) `filename` `]`
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
- Base Type: [settingnode](#type-settingnode)

As Text: Same as `Text`

### Members
- ??? `Text[`???`]`

### Methods
- `Set[`???`]`



## Type: settingsetref
- Base Type: [settingset](#type-settingset)

### Initializers
`settingsetref`
- `settingsetref[` [uint](#type-uint) `]`

### Members
- ??? `GUID[`???`]`

### Methods
- `Set[`???`]`



## Type: agentprovider

As Text: "agentprovider"

### Members
- [uint](#type-uint) `ID`
- [unistring](#type-unistring) `Name`
- [string](#type-string) `URL`
- [unistring](#type-unistring) `Description`
- [agentlisting](#type-agentlisting) `NewestListing`
- [agentlisting](#type-agentlisting) `Listing[` [string](#type-string) `listingCodeName` `]`
- [jsonobject](#type-jsonobject) `Listings`
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `BeginRefresh[`???`]`
- `Remove[`???`]`

### Static Members
- [agentprovider](#type-agentprovider) `New[` [string](#type-string) `filename` `,` <[jsonvalueref](#type-jsonvalueref) `joProvider`> `]`
- [agentprovider](#type-agentprovider) `Get[` [string](#type-string) `name` `]`
- [agentprovider](#type-agentprovider) `Get[` [uint](#type-uint) `id` `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: For each listing in the provider, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration



## Type: agentlisting

As Text: "agentprovider"

### Members
- [unistring](#type-unistring) `CodeName`
- [unistring](#type-unistring) `Name`
- [unistring](#type-unistring) `Version`
- [string](#type-string) `URL`
- [unistring](#type-unistring) `Description`
- [uint](#type-uint) `MinimumBuild`
- [agentprovider](#type-agentprovider) `Provider`
- [bool](#type-bool) `HasDownload`
- [jsonobject](#type-jsonobject) `Collection`
- [jsonobject](#type-jsonobject) `DownloadedCollection`
- [bool](#type-bool) `Downloaded`
- [bool](#type-bool) `Downloading`
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `BeginDownload[`???`]`
- `Install[` <[bool](#type-bool) `installCollection`=false> `,` <[string](#type-string) `listingCodeName`> `]`
- `InstallFromCollection[`???`]`



## Type: dotnet
- Static: Yes (All Members/Methods also work as Static Members/Methods)

### Members
- [bool](#type-bool) `Ready`
- [jsonarray](#type-jsonarray) `Domains`
- [bool](#type-bool) `Domain[` [string](#type-string) `name` `]`

### Methods
- `Execute[` [string](#type-string) `name` `,` [string](#type-string) `executable` `,` ... [string](#type-string) `params` `]`
- `Unload[` [string](#type-string) `name` `]`



## Type: distributedscope
A Distributed Scope works like a jsonobject, with values distributed among a specified set of sessions depending on `Distribution`.

As Text: "distributedscope"

### Members
- [uint](#type-uint) `ID`
- [string](#type-string) `Name`
- [distributedvalue](#type-distributedvalue) `Get[` [string](#type-string) `key` `]`: The distributedvalue with the given key
- [int64](#type-int64) `GetInteger[` [string](#type-string) `key` `]`: The int64 representation of the value with the given key
- [bool](#type-bool) `GetBool[` [string](#type-string) `key` `]`: The bool representation of the value with the given key
- [float64](#type-float64) `GetNumber[` [string](#type-string) `key` `]`: The float64 representation of the value with the given key
- [jsonarray](#type-jsonarray) `Values[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: A jsonarray containing the values in the scope
- [string](#type-string) `Distribution`: A Relay target used to distribute the value (e.g. "all")
- [jsonobject](#type-jsonobject) `AsJSON`: A JSON object describing the Distributed Scope and containing its values
- [bool](#type-bool) `Has[` [string](#type-string) `key` `]`: TRUE if the scope contains a value by the given key
- [bool](#type-bool) `Assert[` [jsonvalue](#type-jsonvalue) `json` `]`: TRUE if the scope contains a value by the given key, which exactly matches the provided JSON value
- [jsonarray](#type-jsonarray) `Keys[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: An array of all keys in the scope
- [int64](#type-int64) `Size`: Number of values in the scope
- [int64](#type-int64) `Used`: Number of values in the scope
- [event](#type-event) `OnUpdateReceived`: Fires when the distributed scope has been updated from a remote source
- [event](#type-event) `OnValueAdded`: Fires when a new value is added to the scope
- [event](#type-event) `OnValueRemoved`: Fires when a value is removed from the scope
- [event](#type-event) `OnValueChanged`: Fires when a value is replaced

### Methods
- `Clear`: Clears (removes) all values from the distributed scope
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`: For each value in the scope, performs the specified code. The [[TLO:ForEach|ForEach Top-Level Object]] is used to access the Key or Value for each iteration
- `Set[` <"-lazy"> `,` [string](#type-string) `name` `,` [jsonvalue](#type-jsonvalue) `newValue` `]`
- `SetString[` [string](#type-string) `name` `,` [string](#type-string) `value` `]`
- `SetInteger[` [string](#type-string) `name` `,` [int64](#type-int64) `value` `]`
- `SetBool[` [string](#type-string) `name` `,` [bool](#type-bool) `value` `]`
- `SetNumber[` [string](#type-string) `name` `,` [float64](#type-float64) `value` `]`
- `SetNULL[` [string](#type-string) `name` `]`
- `Erase[` [string](#type-string) `name` `]`: Removes a distributed value from the scope
- `Push`: Explicitly pushes the entire distributed scope. This should not normally be necessary, as sets of changes are generally distributed.
- `SetValues[` [string](#type-string) `jsonobject` `]`: Applies changes to multiple values, as specified by a JSON object
- `Remove`: Destroys this Distributed Scope

### Static Members
- [distributedscope](#type-distributedscope) `Get[` [string](#type-string) `name` `]`: Retrieves a Distributed Scope by name
- [distributedscope](#type-distributedscope) `Get[` [uint](#type-uint) `id` `]`: Retrieves a Distributed Scope by ID
- [distributedscope](#type-distributedscope) `New[` [jsonobject](#type-jsonobject) `json` `]`: Adds a Distributed Scope, given JSON to initialize with
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`
- [anonevent](#type-anonevent) `OnScopeAdded`: Event fires when a Distributed Scope is added
- [anonevent](#type-anonevent) `OnScopeRemoved`: Event fires when a Distributed Scope is removed

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: distributedvalue

As Text: Same as `Value`

### Members
- [string](#type-string) `Name`: Name of the distributed value
- [jsonvalue](#type-jsonvalue) `Value`: The distributed value
- [event](#type-event) `OnValueChanged`: Fires when the Value is replaced. This event will not fire if an object or array are *modified*, only if they are *replaced*.
- [distributedscope](#type-distributedscope) `Scope`
- [jsonvalue](#type-jsonvalue) `AsJSON`

### Methods
- `Remove`: Removes the value from the distributed scope
- `Push`: Distributes this individual value. Note that a manual Push is not necessary for most cases, but may be useful when modifying a json object or array (as doing so will not automatically Push).




---
# JSON Definitions
## Definition: joystickDefinition
```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "integer",
      "default": 1,
      "description": "If not specified, the joystick will define the first joystick (#1)"
    },
    "systemId": {
      "type": "integer",
      "default": 0,
      "description": "If not specified, the joystick will not refer to a system joystick"
    },
    "name": {
      "type": "string",
      "default": "Virtual Joystick"
    },
    "hasPOV": {
      "type": "boolean",
      "default": true
    },
    "hasZ": {
      "type": "boolean",
      "default": true
    },
    "hasR": {
      "type": "boolean",
      "default": true
    },
    "hasU": {
      "type": "boolean",
      "default": true
    },
    "hasV": {
      "type": "boolean",
      "default": true
    },
    "numButtons": {
      "type": "integer",
      "default": 32
    },
    "numAxes": {
      "type": "integer",
      "default": 6
    },
    "mid": {
      "type": "integer",
      "default": 0,
      "description": "Manufacturer ID number"
    },
    "pid": {
      "type": "integer",
      "default": 0,
      "description": "Product ID number"
    }
  }
}
```

Inner Space Uplink API Specification (LavishScript)

---
# Events
## Event: GamesChanged

## Event: OnSessionConnected

## Event: OnSessionRenamed

## Event: OnSessionDisconnected

## Event: OnSessionsUpdated

## Event: OnRemoteSessionConnected
- Restricted: Yes

## Event: OnRemoteSessionDisconnected
- Restricted: Yes

## Event: OnUplinkConnected
- Restricted: Yes

## Event: OnUplinkRenamed
- Restricted: Yes

## Event: OnUplinkDisconnected
- Restricted: Yes


---
# Commands
## Command: MainWindow
### Syntax
* `MainWindow` "-show"|"-hide"|"-toggle"

## Command: WindowSize
### Syntax
* `WindowSize`
* `WindowSize` ["-rescale"] "-fullscreen"|"-reset"
* `WindowSize` ["-rescale"] ["-viewable"] <[string](#type-string) `widthAndHeight`>

## Command: Speak
### Syntax
* `Speak` ["-async"] ["-volume" <[float](#type-float) `newVolume`>] ["-speed" <[float](#type-float) `newSpeed`>] <[string](#type-string) `text`>

## Command: RestoreGamma
### Syntax
* `RestoreGamma`

## Command: RelayGroup
### Syntax
* `RelayGroup` "-list"|"-clear"
* `RelayGroup` "-join"|"-leave" <[string](#type-string) `name`>

## Command: Name
### Syntax
* `Name` <[string](#type-string) `name`>
  * Sets the Name of the current Session (must be sent from a local Session)

## Command: RelayTargets
### Syntax
* `RelayTargets` <[string](#type-string) `relayTarget`>

## Command: Sessions
### Syntax
* `Sessions`

## Command: Kill
### Syntax
* `Kill` <[string](#type-string) `sessionName`>

## Command: Attach
### Syntax
* `Attach` <[uint](#type-uint) `pid`> [[string](#type-string) `gameName`="Generic"] [[string](#type-string) `gameProfileName`="Generic Default Profile"] [... `startupOptions` ["-loader" "none"|"minimum"|"moderate"|"standard"|"maximum"|"-startup" <[string](#type-string) `command`>|"-prestartup" <[string](#type-string) `command`>|"-character" <[int64](#type-int64) `characterID`>]]

## Command: Launch
### Syntax
* `Launch` <[string](#type-string) `gamePath`> <[string](#type-string) `gameExecutable`> [[string](#type-string) `gameParameters`] [... `startupOptions` ["-loader" "none"|"minimum"|"moderate"|"standard"|"maximum"|"-nogameprofileparams"|"-addparam" <[string](#type-string) `value`>|"-startup" <[string](#type-string) `command`>|"-prestartup" <[string](#type-string) `command`>|"-character" <[int64](#type-int64) `characterID`>|"-loaderflags" <[string](#type-string) `binary representation of flag changes`>]]

## Command: Open
### Syntax
* `Open` <[string](#type-string) `gameName`> <[string](#type-string) `gameProfileName`> [... `startupOptions` ["-loader" "none"|"minimum"|"moderate"|"standard"|"maximum"|"-nogameprofileparams"|"-addparam" <[string](#type-string) `value`>|"-startup" <[string](#type-string) `command`>|"-prestartup" <[string](#type-string) `command`>|"-character" <[int64](#type-int64) `characterID`>|"-loaderflags" <[string](#type-string) `binary representation of flag changes`>]]

## Command: Focus
### Syntax
* `Focus` <[string](#type-string) `sessionName`>
* `Focus` "-next"|"-previous"|"-first"|"-last" [[string](#type-string) `filter`]

## Command: MakeShortcut
### Syntax
* `MakeShortcut` <[string](#type-string) `gameName`> <[string](#type-string) `gameProfileName`>

## Command: RemoteUplink
- Restricted: Yes

### Syntax
* `RemoteUplink` "-list"
* `RemoteUplink` "-connect" <[string](#type-string) `hostname`> [[uint](#type-uint) `port`]
* `RemoteUplink` "-disconnect" <[string](#type-string) `nameOrIP`>


---
# Top-Level Objects
## TLO: LicenseServer
- [licenseserver](#type-licenseserver) `LicenseServer`

## TLO: Sessions
- [uint](#type-uint) `Sessions`

## TLO: Session
- [session](#type-session) `Session[` [uint](#type-uint) `index` `]`
- [session](#type-session) `Session[` [string](#type-string) `name` `]`

## TLO: RemoteUplink
- Restricted: Yes

## TLO: ISMenu
- [ismenu](#type-ismenu) `ISMenu`
- [ismenuitem](#type-ismenuitem) `ISMenu[` [uint](#type-uint) `id` `]`
- [ismenuitem](#type-ismenuitem) `ISMenu[` [string](#type-string) `name` `]`

## TLO: VideoFeed
- [videofeed](#type-videofeed) `VideoFeed`

## TLO: Speech
- [speech](#type-speech) `Speech`

## TLO: ISUplink
- [innerspaceuplink](#type-innerspaceuplink) `ISUplink`


---
# Enums
none.

---
# Types
## Type: licenseserver
- Static: Yes (All Members/Methods also work as Static Members/Methods)

### Members
- [uint](#type-uint) `CheckPatchTime`
- [string](#type-string) `ExpirationDate`
- [int](#type-int) `PatchFiles`
- [jsonobject](#type-jsonobject) `LiveBuild`
- [jsonobject](#type-jsonobject) `DevBuild`
- [bool](#type-bool) `UseDevBuild`

### Methods
- `CheckPatch[`???`]`
- `ApplyPatch[` [string](#type-string) `branch` `,` [string](#type-string) `version` `]`



## Type: session

As Text: Same as `Name`

### Members
- [string](#type-string) `Name`
- [bool](#type-bool) `IsLocal`
- [uint](#type-uint) `PID`
- [gdiwindow](#type-gdiwindow) `Window`
- [filepath](#type-filepath) `Executable`
- [jsonobject](#type-jsonobject) `AsJSON`
- [uint](#type-uint) `Slot`

### Methods
- `Execute[` <"-noredirect"> `,` [string](#type-string) `command` `]`
- `Kill`

### Static Members
- [session](#type-session) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`
- [event](#type-event) `OnSessionAdded`: Same as Event[OnSessionConnected]
- [event](#type-event) `OnSessionRemoved`: Same as Event[OnSessionDisconnected]
- [event](#type-event) `OnSessionRenamed`: Same as Event[OnSessionRenamed]

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: remoteuplink
- Restricted: Yes

As Text: Same as `Name`

### Members
- [string](#type-string) `Name`
- [string](#type-string) `IPAddress`
- [uint](#type-uint) `Sessions`
- [session](#type-session) `Session[` [uint](#type-uint) `nthSession` `]`

### Methods
- `Execute[` <"-noredirect"> `,` [string](#type-string) `command` `]`



## Type: speech
- Static: Yes (All Members/Methods also work as Static Members/Methods)

### Members
- ??? `Ready[`???`]`

### Methods
- `Speak[`???`]`
- `Initialize[`???`]`
- `Stop[`???`]`
- `DumpVoices[`???`]`



## Type: relaygroup

As Text: Same as `Name`

### Members
- ??? `Name[`???`]`
- ??? `Members[`???`]`
- ??? `AsJSON[`???`]`

### Methods
- `AddMember[`???`]`
- `RemoveMember[`???`]`
- `Execute[`???`]`

### Static Members
- [relaygroup](#type-relaygroup) `New[` [string](#type-string) `name` `]`
- [relaygroup](#type-relaygroup) `Get[` [string](#type-string) `name` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: sessionlauncher

### Initializers
- `sessionlauncher[` [weakref](#type-weakref) `ref` `]`

### Members
- [sessionlauncher](#type-sessionlauncher) `Reference`
- [int64](#type-int64) `ID`
- [string](#type-string) `Game`
- [string](#type-string) `GameProfile`
- [string](#type-string) `Executable`
- [string](#type-string) `Path`
- [string](#type-string) `Parameters`
- [jsonobject](#type-jsonobject) `Data`: (return: see JSON definition [sessionlauncher.new](#definition-sessionlaunchernew))
- [uint](#type-uint) `ProcessID`
- [string](#type-string) `Error`
- [bool](#type-bool) `IsStarted`
- [bool](#type-bool) `IsCompleted`
- [bool](#type-bool) `Success`
- [int](#type-int) `ResultCode`
- [time](#type-time) `StartTime`
- [jsonobject](#type-jsonobject) `Metadata`
- [jsonobject](#type-jsonobject) `AsJSON`: (return: see JSON definition [sessionlauncher](#definition-sessionlauncher))
- [anonevent](#type-anonevent) `OnLaunchStarted`
- [anonevent](#type-anonevent) `OnLaunchFailed`
- [anonevent](#type-anonevent) `OnLaunchSucceeded`

### Methods
- `SetReference[` [weakref](#type-weakref) `ref` `]`
- `Abort`
- `Start`

### Static Members
- [sessionlauncher](#type-sessionlauncher) `New[` [jsonvalueref](#type-jsonvalueref) `json` `]`: (json: see JSON definition [sessionlauncher.new](#definition-sessionlaunchernew))
- [sessionlauncher](#type-sessionlauncher) `Get[` [int64](#type-int64) `id` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`
- [anonevent](#type-anonevent) `OnSessionLauncherAdded`
- [anonevent](#type-anonevent) `OnSessionLauncherRemoved`

### Static Methods
- `Launch[` [jsonvalueref](#type-jsonvalueref) `joLaunchDetails` `]`: (joLaunchDetails: see JSON definition [sessionlauncher.new](#definition-sessionlaunchernew))
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: slotobserver

### Initializers
- `slotobserver[` [weakref](#type-weakref) `ref` `]`

### Members
- [slotobserver](#type-slotobserver) `Reference`
- [uint](#type-uint) `Slot`
- [sessionlauncher](#type-sessionlauncher) `NewLauncher[` [jsonvalueref](#type-jsonvalueref) `joLauncherInfo` `]`: Returns a new sessionlauncher, for this slot, if there is not already a sessionlauncher in progress for the slot (joLauncherInfo: see JSON definition [sessionlauncher.new](#definition-sessionlaunchernew))
- [anonevent](#type-anonevent) `OnSessionAdded`
- [anonevent](#type-anonevent) `OnSessionLost`
- [anonevent](#type-anonevent) `OnMainSessionUpdated`
- [anonevent](#type-anonevent) `OnMainSessionLost`
- [jsonobject](#type-jsonobject) `Sessions`
- [session](#type-session) `MainSession`
- [jsonobject](#type-jsonobject) `Metadata`
- [jsonobject](#type-jsonobject) `AsJSON`

### Methods
- `SetReference`
- `Launch[` [jsonvalueref](#type-jsonvalueref) `joLauncherInfo` `]`: Initiates a launch via new sessionlauncher, for this slot, if there is not already a sessionlauncher in progress for the slot (joLauncherInfo: see JSON definition [sessionlauncher.new](#definition-sessionlaunchernew))
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`

### Static Members
- [slotobserver](#type-slotobserver) `New[` [uint](#type-uint) `slotNumber` `]`
- [slotobserver](#type-slotobserver) `Get[` [uint](#type-uint) `slotNumber` `]`
- [jsonarray](#type-jsonarray) `List[` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`
- [anonevent](#type-anonevent) `OnSlotObserverAdded`
- [anonevent](#type-anonevent) `OnSlotObserverRemoved`

### Static Methods
- `ForEach[` [string](#type-string) `command` `,` <[jsonvalueref](#type-jsonvalueref) `filterQuery`> `]`



## Type: innerspaceuplink
- Static: Yes (All Members/Methods also work as Static Members/Methods)

### Members
- ??? `Game[`???`]`
- ??? `Games[`???`]`
- ??? `RelayGroup[`???`]`
- ??? `RelayGroups[`???`]`
- ??? `Session[`???`]`
- ??? `Sessions[`???`]`

### Methods
- `Resolve[`???`]`
- `AddGame[`???`]`
- `AddRelayGroup[`???`]`
- `RemoveGame[`???`]`



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
- ??? `AsJSON[`???`]`

### Methods
- `SetCheck[`???`]`
- `Remove[`???`]`
- `Rename[`???`]`



## Type: ismenu


### Members
- ??? `AddCommand[`???`]`
- ??? `AddSeparator[`???`]`
- ??? `AddSubMenu[`???`]`
- [ismenuitem](#type-ismenuitem) `AddFromJSON[` `jsonobject` `]`
- ??? `Children[`???`]`
- ??? `FindChild[`???`]`
- ??? `ChildCount[`???`]`

### Methods
- `Clear[`???`]`
- `AddCommand[`???`]`
- `AddSeparator[`???`]`
- `AddSubMenu[`???`]`
- `AddFromJSON[` [jsonobject](#type-jsonobject) `]`
- `AddFromJSON[` [jsonarray](#type-jsonarray) `]`



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
- Static: Yes (All Members/Methods also work as Static Members/Methods)

### Members
none.
### Methods
- `RegisterSource[`???`]`
- `RegisterOtherWindowSource[`???`]`
- `RegisterOutput[`???`]`
- `UnregisterSource[`???`]`
- `UnregisterOutput[`???`]`
- `DumpSources[`???`]`
- `DumpOutputs[`???`]`




---
# JSON Definitions
## Definition: sessionlauncher.new
```json
{
  "type": "object",
  "properties": {
    "game": {
      "type": "string",
      "description": "The Inner Space Game to use for launch settings",
      "default": "Generic"
    },
    "gameProfile": {
      "type": "string",
      "description": "If provided, the Inner Space Game Profile to use (from the 'game')"
    },
    "path": {
      "type": "string",
      "description": "The path to the executable to launch, overriding Game Profile settings"
    },
    "executable": {
      "type": "string",
      "description": "The executable filename to launch, overriding Game Profile settings"
    },
    "parameters": {
      "type": "string",
      "description": "The full parameters to pass to the executable, overriding Game Profile settings"
    },
    "slot": {
      "type": "integer",
      "description": "The pre-determined Slot number, overriding default session numbering behavior"
    },
    "killBeforeLaunch": {
      "type": "string",
      "description": "An executable filename to kill before launching this one, overriding Game Profile settings. This can be used to help make sure only one instance of a game launcher is running, etc."
    },
    "metadata": {
      "type": "object",
      "description": "Metadata to provide to the new Session, to be accessible within the Session via innerspacesession.Metadata"
    }
  }
}
```
## Definition: sessionlauncher
```json
{
  "type": "object",
  "properties": {
    "data": {
      "$ref": "#/definitions/sessionlauncher.new"
    },
    "processId": {
      "type": "integer"
    },
    "started": {
      "type": "boolean"
    },
    "completed": {
      "type": "boolean"
    },
    "succeeded": {
      "type": "boolean"
    },
    "resultCode": {
      "type": "integer"
    },
    "error": {
      "type": "string"
    },
    "gameProfileId": {
      "type": "integer"
    }
  }
}
```

