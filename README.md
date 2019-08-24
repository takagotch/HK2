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
    
    
    
    
    
  }
  
  
}

```

```
```

```
```


