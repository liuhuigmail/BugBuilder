```diff
diff --git a/defects4j/jsoup_93_fix/src/main/java/org/jsoup/nodes/FormElement.java b/defects4j/jsoup_93_buggy/src/main/java/org/jsoup/nodes/FormElement.java
index 5770289..3949f22 100644
--- a/defects4j/jsoup_93_fix/src/main/java/org/jsoup/nodes/FormElement.java
+++ b/defects4j/jsoup_93_buggy/src/main/java/org/jsoup/nodes/FormElement.java
@@ -86,7 +86,6 @@ public class FormElement extends Element {
             if (name.length() == 0) continue;
             String type = el.attr("type");
 
-            if (type.equalsIgnoreCase("button")) continue; // browsers don't submit these
 
             if ("select".equals(el.normalName())) {
                 Elements options = el.select("option[selected]");
```
