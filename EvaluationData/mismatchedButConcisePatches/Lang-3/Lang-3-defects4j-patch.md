```diff
diff --git a/defects4j/lang_3_fix/src/main/java/org/apache/commons/lang3/math/NumberUtils.java b/defects4j/lang_3_buggy/src/main/java/org/apache/commons/lang3/math/NumberUtils.java
index 1e6ccdc0..c5840215 100644
--- a/defects4j/lang_3_fix/src/main/java/org/apache/commons/lang3/math/NumberUtils.java
+++ b/defects4j/lang_3_buggy/src/main/java/org/apache/commons/lang3/math/NumberUtils.java
@@ -590,22 +590,18 @@ public class NumberUtils {
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
-            }
         } catch (final NumberFormatException nfe) { // NOPMD
             // ignore the bad number
         }
```
