# User interface framework: bajaux
## What is bajaux?
+ is an HTML5 widget framework
+ that integrates with the Niagara Framework
+ We used it to write a new Property Sheet, Web Charts, Search, and more

## What is a Widget?
+ Self-contained UI element in the browser.
+ Can be small and simple, like a button.
+ Or made of many child Widgets, like a Property Sheet.
+ It can hold a data value.
+ It can integrate with Workbench, the web Profile, Px, and Hx.

## Key APIs
### Widget
...

### fe
...

## bajaux Workflow
1. make a widget
2. Bind it to an element in your page
3. Load in a value
4. Read it back out
5. Save changes

## bajaux Override Points
+ doInitialize()
+ doLoad()
+ doRead()
+ doSave()
+ doDestroy()

## Example Widget
```javascript
fe.buildFor({
  value: 50,
  dom: $('#slider'),
  type: RangeSlider,
  properties: { min: 0, max: 100 }
});
```

## properties()
...

## Framework integration
Create a Java class that tells the framework where to find your JS code. Register it as an agent on a Type.
```javascript
@NiagaraType( agent = @AgentOn(types={"control:NumericPoint"}) )
public class BSimpleGauge extends BSingleton 
  implements BIJavaSript, BIFormFactorMini {
  @Override
  public JsInfo getJsInfo(Context cx) { return JS_INFO; }

  private static final JsInfo JS_INFO = JsInfo.make(
    BOrd.make("module://webEditors/rc/gauge/SimpleGauge.js");
  );
}
```

## Workbench integration
### Commands
...

### Events
bajaux Widgets fire events. Workbench can listen for them.
