# Maths with SGDK #

Unlike modern systems the 68000 heart genesis CPU doesn't have native support for float number (and so float operation). GCC can emulate it but this is really slow.

SGDK has very basic fixed point float support with **fix16** and **fix32**.
They are virtual types which internally use s16 (short) and s32 (long) to simulate fixed point float numbers.


| **Type** | **Sign bit** | **Integer bits** | **Float bits** | **Range** |
|:---------|:-------------|:-----------------|:---------------|:----------|
| fix32 | 1 | 21 | 10 | -2097152.000 --> 2097151.000 |
| fix16 | 1 | 9 | 6 | -512.00 --> 511.00 |


## Declaration ##

You can declare fix16 or fix32 variables this way :

```
  fix16 value_f16;
  fix32 value_f32;
```

### Assigning from constants ###

```
  value_f16 = FIX16(10.5);
  value_f16 = FIX16(2500.5);       // incorrect, out of fix16 range
  value_f32 = FIX32(3456.234);
```

### Assigning from integer ###

```
  s16 value_s16;
  s32 value_s32;
 
  value_s16 = 18;
  value_s32 = 123;

  // convert integer to fix16 / fix32
  value_f16 = FIX16(value_s16);
  value_f32 = FIX32(value_s32);
```

### Converting back to integer ###

```
  value_s16 = F16_toInt(value_f16);
  value_s32 = F32_toInt(value_f32);

  // rounded conversion
  value_s16 = F16_toRoundedInt(value_f16);
  value_s32 = F32_toRoundedInt(value_f32);
```

### Converting fix16 to fix32 and vice versa ###

```
  value_f16 = F32_toFix16(value_f32);
  value_f32 = F16_toFix32(value_f16);
```

### Basic math operations ###

```
  fix16 f, f1, f2;
  s16 i;

  f1 = FIX16(5.5);
  f2 = FIX16(2.3);

  // addition f1 + f2 (usual way does work here)
  f = f1 + f2;

  // subtraction f1 - f2 (usual way does work here)
  f = f1 - f2; 

  // multiplication f1 * f2 (usual way *does not work* here)
  f = F16_mul(f1, f2);

  // division f1 / f2 (usual way *does not work* here)
  f = F16_div(f1, f2);

  // get fractional part of f1
  f = F16_frac(f1);

  // get integer part of f1
  f = F16_int(f1);

  // round to nearest integer with fix16 output
  f = F16_round(f1);

  // round to nearest integer with int output
  i = F16_toRoundedInt(f1);
```

Note here than all methods also exists for fix32.<br>
<b>Warning</b> : Multiplication and division operations are a lot faster on fix16 than fix32 so try to use fix16 when possible.<br>
<br>
<h3>Advanced math operations</h3>

<pre><code>// Log2<br>
f = F16_log2(f1);<br>
<br>
// Log10<br>
f = F16_log10(f1);<br>
<br>
// Sqrt<br>
f = F16_sqrt(f1); <br>
</code></pre>

These methods are available only for fix16 as they use tables and this would requires 16 GB for fix32 :p<br>
I plan to implement "software" methods for fix32 later but that would be pretty slow compared to fix16 tables !<br>
<br>
<h3>Trigonometry</h3>

SGDK has basic trigonometric methods:<br>
<br>
<pre><code>F16_sin(v)<br>
F16_cos(v)<br>
F16_tan(v)<br>
F16_atan(v)<br>
F16_atan2(y,x)<br>
F32_sin(v)<br>
F32_cos(v)<br>
</code></pre>

All the basic mathematical stuff is defined in "maths" unit (maths.h and maths.c files).