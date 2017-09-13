# Web Architecture
## Servlet Component
### 1 Create a module
Use Niagara Workbench New Module Wizard in Tools Menu.

### 2 Annotation code
```java
@NiagaraType
@NiagaraProperty(
        name = "servletName",
        type = "baja:String",
        flags = Flags.HIDDEN | Flags.READONLY,
        defaultValue = "myServlet"
)
public class BMyServlet extends BWebServlet {
  
}
```

### 3 slot-o-matic
Run the slot-o-matic tool to generate codes

### 4 Override doGet() method
```java
@Override
  public void doGet(WebOp c) throws Exception {
    c.setContentType("text/html; charset=utf-8");
    c.getWriter().write("<!DOCTYPE html><html><body><h1>Hello Web Servlet!</h1></body></html>");
  }
```

### 5 Add to the module's palette
...

### 6 Build
...

## Servlet As Views
...

## Standard Java Servlet
...

## Niagara RPC

