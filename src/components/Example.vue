<template>
    <div class="app-container">
        <h3>Vue form generator element example</h3>
        <el-form :model="model">
            <VueFormGenerator :schema='schema' :model='model' :options="formOptions"></VueFormGenerator>
            <el-form-item>
                <el-button type="primary" @click="">Save</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
    import {component as VueFormGenerator} from 'vue-form-generator'

    export default {
        components: {VueFormGenerator},
        name: 'Example',
        data() {
            return {
                model: {
                    // input_number: 111777,
                    // switch_val:'valueOff'
                    // input_date_time:'2019-03-11T11:00:00'
                    color:'#ffd700',
                    // select:1
                },
                schema: {
                    groups: [
                        {
                        styleClasses: 'none',
                        fields: [
                            {
                                type: 'elementInput',
                                model: 'input_number',
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
                                elementLabel: 'Input number example',
                                placeholder: 'Input number example',
                                min: 0,
                                max:10,
                                autocomplete: 'on',
                                alt: 'Input number alt',
                                clearable: true,


                            },
                            {
                                type: 'elementSwitch',
                                model: 'switch_val',
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
                                model: 'input_date_time',
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
                                elementLabel: 'Date picker example',
                                placeholder: 'Date picker example',
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


                            // {
                            //     type: "input",
                            //     inputType: "text",
                            //     label: "Name",
                            //     id: "full_name",
                            //     readonly: false,
                            //     featured: true,
                            //     disabled: false,
                            //     required: true,
                            //     default: "Anonymous",
                            //     model: "input",
                            //     hint: "Please enter your full name",
                            //     help: "This is an other longer help text",
                            // }
                        ],
                    }
                    ]
                },
                formOptions: {
                    validateAfterLoad: true,
                    validateAfterChanged: true
                }

            }
        }
    }
</script>

<style>
    .none {
        border: none;
    }
</style>

