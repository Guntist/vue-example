<template>
    <div class="container">
        <h1 contenteditable="true">{{ messageObj.text }}</h1>
        <button @click="getData">
            get data
        </button>
        <button @click="setError">
            get data Error
        </button>
        <ul class="list-group">
            <li class="list-group-item" v-for="(item, index) in log" :key="index"> {{ item }} </li>
        </ul>
        <modal v-if="showModal" title="Error" :body="errorMsg" @close="showModal = false">
            <h3 slot="header">Error</h3>
        </modal>
    </div>
</template>

<script>
import HttpCaller from '../common/service/Http';
import { CustomModal } from '../common/component/index';
import { MaintEventType, ErrorEventType } from '../common/EventConstant';

export default {
    name: 'ServiceCaller',
    data () {
        return {
            messageObj: {
                id: '01',
                text: 'Service Caller Example',
                author: 'kenneth'
            },
            log: [],
            showModal: false,
            errorMsg: ''
        };
    },
    components: {
        CustomModal
    },
    methods: {
        getData () {
            HttpCaller.service('testAction', 'get', 'http://jsonplaceholder.typicode.com/posts', {});
        },
        setError () {
            HttpCaller.service('testAction', 'get', 'http://jsonplaceholder.typicode.com/getsss', {});
        },
        bindService (event) {
            console.log('response : ', event);
            this.log = event.detail.data;
        },
        showError (event) {
            this.errorMsg = `<span>URI : ${event.detail.uri} <br/> Message: <br/> <h5> ${event.detail.message} </h5></span>`;
            this.showModal = true;
            console.log('showError : ', event);
        }
    },
    beforeCreate () {
        console.log('beforeCreate');
    },
    created () {
        console.log('created');
        addEventListener(MaintEventType.MAIN_EVENT, this.bindService);
        addEventListener(ErrorEventType.SERVER_ERROR, this.showError);
    },
    beforeMount () {
        console.log('beforeMount');
    },
    updated () { // when view data update ( re rendering )
        console.log('updated');
    },
    mounted () {
        console.log('mounted');
        // this.$nextTick(function () {
        // });
    },
    beforeDestroy () {
        console.log('beforeDestroy');
    },
    destroyed () {
        console.log('destroyed');
        removeEventListener(MaintEventType.MAIN_EVENT, this.bindService);
        removeEventListener(ErrorEventType.SERVER_ERROR, this.showError);
    },
    errorCaptured (error, vm, info) {
        console.log('errorCaptured : ', error, vm, info);
        return false;
    }
};
</script>
