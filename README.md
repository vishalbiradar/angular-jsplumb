# Angular Jsplumb Integration

#### To use this repo code as it is, follow the below steps

- clone this repo
- do npm install
- npm start

#### To Integrate jsplumb in your any angular project, follow below steps

Steps to integrate JsPlumb:

1) install the jsplumb package  

    ```sh
    npm install jsplumb --save
    ```
    
2) add jsplumb js file in the index page or in the angular-cli.json file

    In index.html  
    ```html
    <script href="../node_modules/jsplumb/dist/js/jsplumb.min.js"></script>
    ```
    
    or
    
    In angular-cli.json
    
    ```js 
    "scripts": [
             "../node_modules/jsplumb/dist/js/jsplumb.min.js"
      ],
      ```

3) declare jsplumb in your component class where you are going to write the 
actual jsplumb connection logic  

    ```js
    declare var jsPlumb: any;
    ```

4) initialize the jsplumb instance inside AfterViewInit hook of angular.
    ```js
    jsPlumbInstance;
    
     ngAfterViewInit() {
         this.jsPlumbInstance = jsPlumb.getInstance();
     }
     ```
     
5) start writing the actual jsplumb logic (for ex. connecting two elements)
    ```js
    connectSourceToTargetUsingJSPlumb() {
        let labelName;
          labelName = 'connection';
          this.jsPlumbInstance.connect({
            connector: ['Flowchart', {stub: [212, 67], cornerRadius: 1, alwaysRespectStubs: true}],
            source: 'Source', // it is the id of source div
            target: 'Target1', // it is the id of target div
            anchor: ['Right', 'Left'],
            paintStyle: {stroke: '#456', strokeWidth: 4},
            overlays: [
              ['Label', {label: labelName, location: 0.5, cssClass: 'connectingConnectorLabel'}]
            ],
          });
      }
    ```
    
6) The html code
```html
<div class="container">
  <span class="btn btn-primary" (click)="connectSourceToTargetUsingJSPlumb()">Connect</span>
  <div class="row">
    <div class="col-md-12">
      <div class="alignleft">
        <div class="customBox" id="Source">
          Source
        </div>
      </div>
      <div class="alignright">
        <div class="customBox" id="Target1">
          Target 1
        </div>
      </div>
      <div style="clear: both;"></div>
    </div>
  </div>
</div>
```

