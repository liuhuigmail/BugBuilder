```diff
diff --git a/defects4j/lang3fix/src/main/java/org/apache/commons/lang3/math/NumberUtils.java b/defects4j/lang3buggy/src/main/java/org/apache/commons/lang3/math/NumberUtils.java
index 1e6ccdc0..064f5043 100644
--- a/defects4j/lang3fix/src/main/java/org/apache/commons/lang3/math/NumberUtils.java
+++ b/defects4j/lang3buggy/src/main/java/org/apache/commons/lang3/math/NumberUtils.java
@@ -482,7 +482,6 @@ public class NumberUtils {
         // if both e and E are present, this is caught by the checks on expPos (which prevent IOOBE)
         // and the parsing which will detect if e or E appear in a number due to using the wrong offset
 
-        int numDecimals = 0; // Check required precision (LANG-693)
         if (decPos > -1) { // there is a decimal point
 
             if (expPos > -1) { // there is an exponent
@@ -494,7 +493,6 @@ public class NumberUtils {
                 dec = str.substring(decPos + 1);
             }
             mant = str.substring(0, decPos);
-            numDecimals = dec.length(); // gets number of digits past the decimal to ensure no loss of precision for floating point numbers.
         } else {
             if (expPos > -1) {
                 if (expPos > str.length()) { // prevents double exponent causing IOOBE
@@ -590,21 +588,17 @@ public class NumberUtils {
         //Must be a Float, Double, BigDecimal
         final boolean allZeros = isAllZeros(mant) && isAllZeros(exp);
         try {
-            if(numDecimals <= 7){// If number has 7 or fewer digits past the decimal point then make it a float
               final Float f = createFloat(str);
               if (!(f.isInfinite() || (f.floatValue() == 0.0F && !allZeros))) {
                    return f;
               }

-            }
         } catch (final NumberFormatException nfe) { // NOPMD
             // ignore the bad number
         }
         try {
-            if(numDecimals <= 16){// If number has between 8 and 16 digits past the decimal point then make it a double
                final Double d = createDouble(str);
                if (!(d.isInfinite() || (d.doubleValue() == 0.0D && !allZeros))) {
                    return d;
               }
 
-             }
         } catch (final NumberFormatException nfe) { // NOPMD
             // ignore the bad number
```
