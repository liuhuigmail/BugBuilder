```diff
diff --git a/defects4j/jacksondatabind_66_fix/src/main/java/com/fasterxml/jackson/databind/deser/std/StdKeyDeserializer.java b/defects4j/jacksondatabind_66_buggy/src/main/java/com/fasterxml/jackson/databind/deser/std/StdKeyDeserializer.java
index d1148bac1..f827c318d 100644
--- a/defects4j/jacksondatabind_66_fix/src/main/java/com/fasterxml/jackson/databind/deser/std/StdKeyDeserializer.java
+++ b/defects4j/jacksondatabind_66_buggy/src/main/java/com/fasterxml/jackson/databind/deser/std/StdKeyDeserializer.java
@@ -8,7 +8,6 @@ import java.net.URI;
 import java.net.URL;
 import java.util.*;
 
-import com.fasterxml.jackson.core.JsonParser;
 import com.fasterxml.jackson.core.JsonProcessingException;
 import com.fasterxml.jackson.core.io.NumberInput;
 import com.fasterxml.jackson.databind.*;
@@ -16,7 +15,6 @@ import com.fasterxml.jackson.databind.annotation.JacksonStdImpl;
 import com.fasterxml.jackson.databind.introspect.AnnotatedMethod;
 import com.fasterxml.jackson.databind.util.ClassUtil;
 import com.fasterxml.jackson.databind.util.EnumResolver;
-import com.fasterxml.jackson.databind.util.TokenBuffer;
 
 /**
  * Default {@link KeyDeserializer} implementation used for most {@link java.util.Map}
@@ -313,13 +311,9 @@ public class StdKeyDeserializer extends KeyDeserializer
             if (key == null) { // is this even legal call?
                 return null;
             }
-            TokenBuffer tb = new TokenBuffer(ctxt.getParser(), ctxt);
-            tb.writeString(key);
             try {
                 // Ugh... should not have to give parser which may or may not be correct one...
-                JsonParser p = tb.asParser();
-                p.nextToken();
-                Object result = _delegate.deserialize(p, ctxt);
+                Object result = _delegate.deserialize(ctxt.getParser(), ctxt);
                 if (result != null) {
                     return result;
                 }

```
