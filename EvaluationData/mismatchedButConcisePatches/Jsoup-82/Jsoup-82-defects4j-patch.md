```diff
diff --git a/defects4j/jsoup_82_fix/src/main/java/org/jsoup/helper/DataUtil.java b/defects4j/jsoup_82_buggy/src/main/java/org/jsoup/helper/DataUtil.java
index f4012fc..dc12cb3 100644
--- a/defects4j/jsoup_82_fix/src/main/java/org/jsoup/helper/DataUtil.java
+++ b/defects4j/jsoup_82_buggy/src/main/java/org/jsoup/helper/DataUtil.java
@@ -168,10 +168,7 @@ public final class DataUtil {
             }
             Charset charset = Charset.forName(charsetName);
             doc.outputSettings().charset(charset);
-            if (!charset.canEncode()) {
                 // some charsets can read but not encode; switch to an encodable charset and update the meta el
-                doc.charset(Charset.forName(defaultCharset));
-            }
         }
         input.close();
         return doc;
```
