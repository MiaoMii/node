## ts源码

```ts

interface eventContent {
    text: string;
    eventType: string;
    messageDemo: string;
}
interface webcomsInterface {
    id: string;
    componentName: string;
    type: string;
    text: string;
    group: string;
    createTime: string;
    image: string;
    initStyle: string;
    description: string;
    options: {
        x: number;
        y: number;
        style: string,
        width: number;
        height: number;
        data: any,
    }
    eventSpecification: {
        inputEvent: eventContent[]
        outputEvent: eventContent[]
    }
    shadow: HTMLElement;

    init: (context: any, jsConfig: any) => void

    close:() =>  void

    propertyChange: (metaData: any) => void

    receiveMssage: (message: string) => void
}

class Webcomponents implements webcomsInterface {
    id = "1";
    componentName = "text文本";
    type = "文本";
    text = "text文本";
    group = "文本";
    createTime = "";
    image = "";
    initStyle = "width: 150px;height: 150px";
    description = "";
    options = {
        x: 0,
        y: 0,
        style: "",
        width: 150,
        height: 150,
        data: {},
    };
    optionsView = {
        jsonpath: {},
    };
    eventSpecification = {
        inputEvent: [
            {
                text: "",
                eventType: "",
                messageDemo: "",
            },
        ],
        outputEvent: [
            {
                text: "",
                eventType: "",
                messageDemo: "",
            },
        ],
    };
    shadow = document.body;
    init(context: any, jsConfig: any) {}
    close() {}
    propertyChange(MetaData: any) {}
    receiveMssage(message: any) {}
}
```



## 编译过后js代码

#### typescript@2.0.0

```js
var Webcomponents = (function () {
    function Webcomponents() {
        this.id = "1";
        this.componentName = "text文本";
        this.type = "文本";
        this.text = "text文本";
        this.group = "文本";
        this.createTime = "";
        this.image = "";
        this.initStyle = "width: 150px;height: 150px";
        this.description = "";
        this.options = {
            x: 0,
            y: 0,
            style: "",
            width: 150,
            height: 150,
            data: {}
        };
        this.optionsView = {
            jsonpath: {}
        };
        this.eventSpecification = {
            inputEvent: [
                {
                    text: "",
                    eventType: "",
                    messageDemo: ""
                },
            ],
            outputEvent: [
                {
                    text: "",
                    eventType: "",
                    messageDemo: ""
                },
            ]
        };
        this.shadow = document.body;
    }
    Webcomponents.prototype.init = function (context, jsConfig) { };
    Webcomponents.prototype.close = function () { };
    Webcomponents.prototype.propertyChange = function (MetaData) { };
    Webcomponents.prototype.receiveMssage = function (message) { };
    return Webcomponents;
}());

```



#### typescript@3.0.5

```js
var Webcomponents = /** @class */ (function () {
    function Webcomponents() {
        this.id = "1";
        this.componentName = "text文本";
        this.type = "文本";
        this.text = "text文本";
        this.group = "文本";
        this.createTime = "";
        this.image = "";
        this.initStyle = "width: 150px;height: 150px";
        this.description = "";
        this.options = {
            x: 0,
            y: 0,
            style: "",
            width: 150,
            height: 150,
            data: {}
        };
        this.optionsView = {
            jsonpath: {}
        };
        this.eventSpecification = {
            inputEvent: [
                {
                    text: "",
                    eventType: "",
                    messageDemo: ""
                },
            ],
            outputEvent: [
                {
                    text: "",
                    eventType: "",
                    messageDemo: ""
                },
            ]
        };
        this.shadow = document.body;
    }
    Webcomponents.prototype.init = function (context, jsConfig) { };
    Webcomponents.prototype.close = function () { };
    Webcomponents.prototype.propertyChange = function (MetaData) { };
    Webcomponents.prototype.receiveMssage = function (message) { };
    return Webcomponents;
}());

```

#### typescript@4.5.5

```js
var Webcomponents = /** @class */ (function () {
    function Webcomponents() {
        this.id = "1";
        this.componentName = "text文本";
        this.type = "文本";
        this.text = "text文本";
        this.group = "文本";
        this.createTime = "";
        this.image = "";
        this.initStyle = "width: 150px;height: 150px";
        this.description = "";
        this.options = {
            x: 0,
            y: 0,
            style: "",
            width: 150,
            height: 150,
            data: {}
        };
        this.optionsView = {
            jsonpath: {}
        };
        this.eventSpecification = {
            inputEvent: [
                {
                    text: "",
                    eventType: "",
                    messageDemo: ""
                },
            ],
            outputEvent: [
                {
                    text: "",
                    eventType: "",
                    messageDemo: ""
                },
            ]
        };
        this.shadow = document.body;
    }
    Webcomponents.prototype.init = function (context, jsConfig) { };
    Webcomponents.prototype.close = function () { };
    Webcomponents.prototype.propertyChange = function (MetaData) { };
    Webcomponents.prototype.receiveMssage = function (message) { };
    return Webcomponents;
}());

```

