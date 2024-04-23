# Logger

This SFDX project is designed to capture information and errors into a Log object. This framework systematically records essential details such as Class Name, Method Name, Line Number, Messages, Context, Stack Trace, and additional pertinent information. Its purpose is to provide comprehensive logging capabilities for efficient monitoring and debugging within the Salesforce environment.

## Usage

To log a simple text

```bash
Logger.getInstance().info('Simple info text').publish();
Logger.getInstance().error('Simple error text').publish();
```

To capture exception information

```bash
try{

}catch(Exception e){
    Logger.getInstance().error(e).publish();
}
```

To capture errors in List<Database.SaveResult>

```bash
Database.SaveResult[] result = Database.update(records, false);
Logger.getInstance().error(result).publish();
```

To log SOQL queries consumed, rows retrieved, CPU time consumed and Heap size use below statement

```bash
Logger.logLimits();
```

Additionally, this framework logs BatchApexErrorEvent platform events, which capture information from all batches raising BatchApexErrorEvent platform events. To utilize this feature, the only requirement is to implement Database.RaisesPlatformEvents on the batch class.

```bash
public class <BatchClassName> implements Database.Batchable<sObject>, Database.RaisesPlatformEvents{

}
```
