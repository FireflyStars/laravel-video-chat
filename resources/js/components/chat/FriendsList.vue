<template>
    <div>
        <div class="friendlist-container">
            <h3 class="text-center bg-white shadow-sm py-2">Friends</h3>
            <div class="friendlist">
                <ul class="list-unstyled">
                    <li @click="friendSelected(index)" v-for="(val,index) in $parent.friends" :key="index" :class="{'bg-primary text-white':val.is_selected,'bg-light':!val.is_selected}" class="friendlist-item my-2 p-2">
                        {{val.name}} <span v-if="val.is_online" class="text-success"><i class="fas fa-globe"></i></span> <span v-if="val.new_message" class="newmessage-blink"><i class="fas fa-envelope-square"></i></span>
                    </li>
                </ul>
            </div>
        </div>
        
    </div>
</template>
<script>
export default {
    name:"FriendsList",
    data() {
        return {
            
        }
    },
    methods: {
        friendSelected(index){
            this.$parent.friends.forEach(element => {
                element.is_selected = false;
            });
            this.$parent.friends[index].is_selected = true;
            this.$parent.friends[index].new_message = false;
            this.$parent.selected_user = this.$parent.friends[index];
        }
    }
    
}
</script>
<style>
    .friendlist-container{
        background: #e6e6e6;
        height: 500px;
        overflow-y: auto;
    }
    .friendlist-item{
        cursor: pointer;
    }
    .newmessage-blink{
        animation: blink 1s linear infinite;;
    }
    @keyframes blink{
        0%{opacity: 0;}
        50%{opacity: .5;}
        100%{opacity: 1;}
    }
</style>