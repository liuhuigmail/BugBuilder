```diff
diff --git a/defects4j/jxpath_21_fix/src/java/org/apache/commons/jxpath/ri/model/beans/PropertyPointer.java b/defects4j/jxpath_21_buggy/src/java/org/apache/commons/jxpath/ri/model/beans/PropertyPointer.java
index f7e2525..52aa39a 100644
--- a/defects4j/jxpath_21_fix/src/java/org/apache/commons/jxpath/ri/model/beans/PropertyPointer.java
+++ b/defects4j/jxpath_21_buggy/src/java/org/apache/commons/jxpath/ri/model/beans/PropertyPointer.java
@@ -149,8 +149,7 @@ public abstract class PropertyPointer extends NodePointer {
      * @return int length
      */
     public int getLength() {
-        Object baseValue = getBaseValue();
-        return baseValue == null ? 1 : ValueUtils.getLength(baseValue);
+        return ValueUtils.getLength(getBaseValue());
     }
 
     /**
```
