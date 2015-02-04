### :extend( *selector* [exact|any] [shallow|deep] [all])
* **exact** [default] - Match complete selectors (```:extend(.button exact)``` matches ```.button {}``` but not ```#main .button a``` - **```:extend(.a .b)``` is considered an exact match to ```.a { .b { } }```)**
* **any** - Match partial selector (```:extend(.button any)``` matches ```.button {}``` **and** ```#main .button a```)
* **shallow** [default] - extend only root properties (```.a:extend(.button shallow)``` will not include hover in ```.button { &:hover { } }```)
* **deep** - extend all nested selectors/properties (```.a:extend(.button deep)``` **will** include hover in ```.button { &:hover { } }```)
* **all** - set "any" and "deep" to true. Extend all matches, partial and exact, and extend all base and nested properties

**Example:**
```
.b:extend(.a);  // because of defaults, exact=true, shallow=true
.b:extend(.a any);  // exact=false, shallow=true
.b:extend(.a deep);  //exact=true, shallow=false
.b:extend(.a all); // exact=false, shallow=false
```
Since ```exact``` and ```shallow``` are default values, they are not needed / supported as explicit keywords, but are listed above to explain the differences in behavior.

#### Related Discussion
[#1155](../../../less.js/issues/1155) [#2101](../../../less.js/issues/2101)
