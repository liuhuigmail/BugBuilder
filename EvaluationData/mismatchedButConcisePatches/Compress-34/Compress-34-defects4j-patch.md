```diff
diff --git a/defects4j/compress_34_fix/src/main/java/org/apache/commons/compress/archivers/zip/X7875_NewUnix.java b/defects4j/compress_34_buggy/src/main/java/org/apache/commons/compress/archivers/zip/X7875_NewUnix.java
index e325b564..14aebab1 100644
--- a/defects4j/compress_34_fix/src/main/java/org/apache/commons/compress/archivers/zip/X7875_NewUnix.java
+++ b/defects4j/compress_34_buggy/src/main/java/org/apache/commons/compress/archivers/zip/X7875_NewUnix.java
@@ -55,7 +55,6 @@ import static org.apache.commons.compress.archivers.zip.ZipUtil.unsignedIntToSig
  */
 public class X7875_NewUnix implements ZipExtraField, Cloneable, Serializable {
     private static final ZipShort HEADER_ID = new ZipShort(0x7875);
-    private static final ZipShort ZERO = new ZipShort(0);
     private static final BigInteger ONE_THOUSAND = BigInteger.valueOf(1000);
     private static final long serialVersionUID = 1L;
 
@@ -144,7 +143,7 @@ public class X7875_NewUnix implements ZipExtraField, Cloneable, Serializable {
      * @return a <code>ZipShort</code> for the length of the data of this extra field
      */
     public ZipShort getCentralDirectoryLength() {
-        return ZERO;
+        return getLocalFileDataLength();
     }
 
     /**

```
