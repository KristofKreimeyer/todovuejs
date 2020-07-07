<template>
    <div class="wrapper">
        <li @click="clicktoFinish" class="list-group-item clearfix">
            <p>{{ title + " Erledigt: " + (done || isFinished ? " Ja " : " Nein ") }}</p>
            <div>
                <span class="pull-right">
                    <button @click="deleteTodo" class="btn btn-default btn-xs">
                        <span class="fa fa-trash"></span>
                    </button>
                </span>
            </div>
        </li>
    </div>
</template>

<script>
	export default {
		name: "Todo",
        props: {
			title: String,
            done: Boolean,
            deleteTodo: Function
        },
        data: () => ({
            isFinished: false
        }),
        methods: {
			clicktoFinish() {
				this.isFinished = this.isFinished !== true;
            }
        }
	}
</script>

<style scoped>

</style>
