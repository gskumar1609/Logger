# Logger

SFDX project to capture errors in to Log object

## Usage

```bash
try{

}catch(Exception e){
    Logger.getInstance().error(e).publish();
}
```
