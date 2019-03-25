<template>
    <div class="app-container">
        <h3>Vue form generator element example</h3>
        <el-form :model="model" label-width="12em">
            <VueFormGenerator :schema='schema' :model='model' :options="formOptions"></VueFormGenerator>
            <el-form-item>
                <el-button type="primary" @click="click">Save</el-button>
                <el-button @click="">Cancel</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
    import {component as VueFormGenerator} from 'vue-form-generator'
    import {pretty} from 'js-object-pretty-print'
    export default {
        components: {VueFormGenerator},
        name: 'Example',
        data() {
            return {
                model: {
                    // input: 111777,
                    // switch:'valueOff'
                    // date:'2019-03-11T11:00:00'
                    color:'#ffd700',
                    // select:1,
                    // textarea:"text",
                },
                schema: {
                    groups: [
                        {
                        styleClasses: 'none',
                        fields: [
                            {
                                type: 'elementInput',
                                model: 'input',
                                id: 'input_id',
                                inputName: 'input_name',
                                featured: true,//not working (bold field)
                                visible: true,
                                disabled: false,
                                required: true,
                                readonly: false,
                                styleClasses:'',
                                // label: 'Input label', //work, but use elementLabel instead
                                // hint: 'input hint', //working, but element ui hasn't hint
                                // help: 'input help', //working, but element ui hasn't help
                                default: 72211,

                                //text, textarea, number
                                inputType: 'number',
                                step: 0.1,
                                elementLabel: 'Input example',
                                placeholder: 'Input example',
                                min: 0,
                                max:10,
                                autocomplete: 'on',
                                alt: 'Input number alt',
                                clearable: true,


                            },
                            {
                                type: 'elementSwitch',
                                model: 'switch',
                                id: 'switch_id',
                                inputName: 'switch_name',
                                //featured: true,//not working (bold field)
                                visible: true,
                                disabled: false,
                                required: false,//not necessary
                                readonly: true,
                                // label: 'Input label', //work, but use elementLabel instead
                                // hint: 'input hint', //working, but element ui hasn't hint
                                // help: 'input help', //working, but element ui hasn't help
                                default: 'valueOn',//not working

                                elementLabel: 'Switch example',
                                textOn: 'On',
                                textOff: 'Off',
                                valueOn: 'valueOn',
                                valueOff: 'valueOff',
                                colorOn: "#409EFF",
                                colorOff: "#000",
                                width: 60,
                            },
                            {
                                type: 'elementCheckbox',
                                model: 'checkbox_val',
                                id: 'checkbox_id',
                                inputName: 'checkbox_name',
                                //featured: true,//not working (bold field)
                                visible: true,
                                disabled: false,
                                required: true,//not necessary
                                // readonly: true,
                                // label: 'Input label', //work, but use elementLabel instead
                                // hint: 'input hint', //working, but element ui hasn't hint
                                // help: 'input help', //working, but element ui hasn't help
                                elementLabel: 'Checkbox example',
                                checkedValue: 123,
                                uncheckedValue: 456,
                                // default: 1234
                            },
                            {
                                type: 'elementDatePicker',
                                model: 'date',
                                //id: 'custom_element_id',//not working with datePicker
                                inputName: 'date_picker_name',
                                featured: true,//not working (bold field)
                                visible: true,
                                disabled: false,
                                required: true,
                                readonly: false,
                                editable: false,
                                // label: 'Input label', //work, but use elementLabel instead
                                // hint: 'input hint', //working, but element ui hasn't hint
                                // help: 'input help', //working, but element ui hasn't help

                                clearable: true,
                                firstDayOfWeek: 1,
                                elementLabel: 'DatePicker example',
                                placeholder: 'DatePicker example',
                                size: 'large',
                                format: 'dd.MM.yyyy HH:mm:ss',
                                align: 'left',
                                dateType: 'datetime',
                                // default: 'December 17, 1995 03:24:00',
                                // defaultValue: '1999-02-12T12:46:00'
                            },
                            {
                                type: 'elementColorPicker',
                                model: 'color',
                                elementLabel: 'ColorPicker example',
                                id: 'color_picker_id',//add id for colorPicker div
                                inputName: 'color_picker_name',//add name for colorPicker div
                                // featured: true,//not working (bold field)
                                visible: true,
                                disabled: false,
                                // required: true,
                                // readonly: false,
                                // editable: false,
                                // label: 'Input label', //work, but use elementLabel instead
                                // hint: 'input hint', //working, but element ui hasn't hint
                                // help: 'input help', //working, but element ui hasn't help
                                size: 'meduium',
                                showAlpha: false,
                                colorFormat: 'hex',
                                popperClass: 'test',
                                predefine: [
                                    '#ff4500',
                                    '#ff8c00',
                                    '#ffd700',
                                    '#90ee90',
                                    '#00ced1',
                                    '#1e90ff',
                                    '#c71585',
                                ],
                                default: '#ff4500'
                            },
                            {
                                type: 'elementRadio',
                                model: 'radio',
                                elementLabel: 'Radio example',
                                // id: 'radio_id',//not working with Radio
                                inputName: 'radio_name',
                                visible: true,
                                disabled: false,
                                values:[{name:'1',label:1},{name:'2',label:2}],
                                size:'medium', //size of the Radio, only works when border is true
                                default: 2,
                                border: true, // only if radioType not button
                                radioType: '',//'button' or other for default
                                textColor: '#ffd700',//only if radioType is button
                                fill: '#ff4500',//only if radioType is button
                            },
                            {
                                type: 'elementSelect',
                                model: 'select',
                                elementLabel: 'Select example',
                                placeholder: 'Select example',
                                id: 'select_id',
                                inputName: 'select_name',
                                visible: true,
                                disabled: false,
                                valueKey: 'value',
                                values:[{name:'1',id:1},{name:'2',id:2}],
                                size:'large',
                                filterable:false,
                                multiple:false,
                                clearable:true,
                                collapseTags:true,
                                multipleLimit:3,
                                autocomplete:'off',
                                allowCreate:false,
                                filterMethod:function(){},
                                remote:false,
                                remoteMethod:function(){},
                                loadingText:'',
                                noMatchText:'',
                                noDataText:'',
                                popperClass:'',
                                reserveKeyword:false,
                                defaultFirstOption:false,
                                popperAppendToBody:false,
                                automaticDropdown:false,
                                default: 2,
                            },
                            {
                                type: 'elementSlider',
                                model: 'slider',
                                elementLabel: 'Slider example',
                                // id: 'slider_id',//not working with Slider
                                // inputName: 'slider_name', //not working with Slider
                                visible: true,
                                disabled: false,
                                min: 10,
                                max: 77,
                                step: 5,
                                debounce: 500,
                                showInput: true,
                                showInputControls: true,
                                inputSize:'large',
                                showStops:false,
                                showTooltip:true,
                                formatTooltip:function(v){return v;},
                                range:false,
                                default: 12
                            },
                            {
                                type: 'elementTextArea',
                                model: 'textarea',
                                elementLabel: 'Textarea example',
                                placeholder: 'Textarea example',
                                id: 'textarea_id',
                                inputName: 'textarea_name',
                                visible: true,
                                disabled: false,
                                autosize: false,
                                rows: 5,
                                default: "default text value"
                            },
                            {
                                type: 'elementUpload',
                                model: 'upload',
                                elementLabel: 'Upload example',
                                placeholder: 'Click to upload',
                                // id: 'upload_id',//not working with Uploader
                                inputName: 'upload_name',
                                action:'https://www.mocky.io/v2/5185415ba171ea3a00704eed',
                                visible: true,
                                disabled: false,
                                onPreview:function(file){console.log(file);},
                                onRemove:function(file, fileList){console.log(file);console.log(fileList);},
                                onSuccess:function(response, file, fileList){console.log(response);console.log(file);console.log(fileList);},
                                onError:function(err, file, fileList){console.log(err);console.log(file);console.log(fileList);},
                                onProgress:function(event, file, fileList){console.log(event);console.log(file);console.log(fileList);},
                                onChange:function(file, fileList){console.log(file);console.log(fileList);},
                                beforeUpload:function(file){console.log(file);},
                                beforeRemove:function(file, fileList){console.log(file);console.log(fileList);},
                                onExceed:function(file, fileList){console.log(file);console.log(fileList);},
                                httpRequest:function(){},
                                thumbnailMode:true,
                                fileList:[{name: 'linux.jpg', url: 'https://upload.wikimedia.org/wikipedia/commons/d/dd/Linux_logo.jpg'}],
                                listType:"text", //picture,picture-card
                                drag:false,
                                multiple:true,
                                limit:3,
                                autoUpload:true,
                            }
                        ],
                    }
                    ]
                },
                formOptions: {
                    validateAfterLoad: true,
                    validateAfterChanged: true
                }

            }
        },
        methods:{
            click:function () {
                let res='';
                let model=this.model
                Object.keys(this.model).forEach(function(key){
                    res+=key+": " + (typeof model[key]==="string"? "\""+model[key]+"\"":model[key])+"<br/>"
                })
                this.$alert(res, 'Form data', {
                    confirmButtonText: 'OK',
                    dangerouslyUseHTMLString: true
                });
            }
        }
    }
</script>

<style>
    .none {
        border: none;
    }

    .el-form-item__content {
        text-align: left;
    }

    .app-container {
        border: 1px solid #ebebeb;
        border-radius: 3px;
        transition: .2s;
        width: 50%;
        margin: 0 auto;
    }
</style>

