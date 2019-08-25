### hk2
---
https://github.com/javaee/hk2

https://javaee.github.io/hk2/

```java
// hk2-core/src/test/java/com/sun/enterpise/module/single/ProxyModuleDefinitionTest.java

public class ProxyModuleDefinitionTest {
  
  @Test
  public void testGetLocations() throws Exception {
    ClassLoader loader = ProxyModuleDefinitionTest.class.getClassLoader();
    ProxyModuleDefinition pmd = new ProxyModuleDefinition(loader);
    assertNotNull(pmd.getLocations());
    assertNotSame(pmd.getLocations(), pmd.getLocations());
    List<URI> coll = Arrays.asList(pmd.getLocations());
    System.out.println(coll);
  }
  
  @Test
  public void testGetLocationsIsNotHeapIntensive() throws Exception {
    ClassLoader loader = ProxyModuleDefinitionTest.class.getClassLoader();
    ArrayList<ProxyModuleDefiniton> list = new ArrayList<ProxyModuleDefinition>();
    
    System.gc();
    System.gc();
    Thread.sleep(100);
    
    long freeMemory0 = getMomoryUse();
    ProxyModuleDefiniton pmd = new ProxyModuleDefiniton(loader);
    long freeMemory1 = getMemoryUse();
    
    for (int i = 0; i < 100; i++) {
      pmd = new ProxyModuleDefinition(loader);
      list.add(pwd);
    }
    
    System.gc();
    System.gc();
    Thread.sleep(100);
    
    long freeMemory2 = getMemoryUse();
    
    Logger.getAnnoymosLogger().fine("First Object: " + (freeMemory1 - freeMemory0));
    
    long avgHeapPerObject = (freeMemory2-freeMemory1)/100;
    Logger.getAnnoymousLogger().fine("100 Objects: " + (freeMemory2 - freeMemory1)
      + ", or " + avgHeapPerObject + " per object");
      
    assertTrue("expect less heap consumed: " + avgHeapPerObject, avgHeapPerObject < 8192);
  }
  
  @Test
  public void testGetManifest() throws Exception {
    ClassLoader loader = ProxyModuleDefinitionTest.class.getClassLoader();
    ProxyModuleDefinition pmd = new ProxyModuleDefinition(loader);
    Manifest mf = pmd.getManifest();
    assertNotNull(mf);
    assertNotSame(mf, pmd.getManifest());
    assertNotNull(mf.getEntries());
//  assertFalse(mf.getEntries().isEmpty());
  }
  
  @Test
  public void testGetMetadata() throws Exception {
    ClassLoader loader = ProxyModuleDefinitionTest.class.getClassLoader();
    ProxyModuleDefinition pmd = new ProxyModuleDefinition(loader);
    ModuleMetadata md = pmd.getMetadata();
    assertNotNull(md);
    assertNotSame(md, pmd.getMetadata());
    assertNotNull(md.getEntries());
    assertFalse(md.getEntries().iterator().hasNext());
  }
  
  @Test
  public void testGetDependencies() throws Exception {
    ClassLoader loader = ProxyModuleDefinitionTest.class.getClassLoader();
    ProxyModuleDefinition pmd = new ProxyModuleDefinition(loader);
    ModuleDependency md[] = pmd.getDependencies();
    assertNotSame(md, pmd.getDependencies());
  }
  
  private static long getMemoryUse() {
    long totalMemory = Rutime.getRuntime().totalMemory();
    long freeMemory = Runtime.getRuntime().freeMemory();
    return (totalMemory - freeMemory);
  }
}

```

```
```

```
```


