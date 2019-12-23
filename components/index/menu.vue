<template>
<div class='m-menu'>
    <dl class="nav"
    @mouseleave="handleLeave"
    >
        <dt>全部分类</dt>
        <dd v-for='(item, idx) in menu'
         :key='idx'
         @mouseenter="handleEnter"
         >
            <i :class='item.type'></i>
            {{item.name}}
            <span class='arrow'></span>
        </dd>
    </dl>
    <div class='detail'
     v-if='kind'
     @mouseenter="handleDetailEnter"
     @mouseleave="handleDetailLeave"
     >
        <template v-for='(item,idx) in curDetail.child'>
            <h4 :key='idx'>{{item.title}}</h4>
            <span v-for='(items,index) in item.childArr' :key='index+10'>{{items}}</span>
        </template>
    </div>
</div>
</template>
<script>
export default{
    data(){
        return {
            kind:'',
            menu:[{
                type:'food',
                name:'美食',
                child:[{
                    title:'美食',
                    childArr:['代金券','甜点饮品','火锅']
                }]
            },{
                type:'takeout',
                name:'外卖',
                child:[{
                    title:'外卖',
                    childArr:['外卖代金券','甜点饮品','火锅']
                }]
            }
            ]
        }
    },
    computed: {
        curDetail(){
            return (this.menu.filter(item=>item.type === this.kind))[0]
        }
    },
    methods:{
        handleEnter(e){
            this.kind=e.target.getElementsByTagName('i')[0].className
        },
        handleLeave(){
            let self = this;
            self.timer = setTimeout(function(){
                self.kind=''
            },200)
        },
        handleDetailEnter(){
            clearTimeout(this.timer);
        },
        handleDetailLeave(){
            this.kind=''
        }
    }
}
</script>