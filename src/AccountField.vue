<template>
    <div class="flex gap-2 items-center">
        <div v-if="prefix" class="italic">
            {{ prefix }}
        </div>
        <div>
            {{ value }}
        </div>
        <div :class="`ml-auto text-xs ${copied ? 'dark:bg-neutral-300 dark:text-black bg-neutral-800 text-white' : 'dark:bg-neutral-800 dark:text-white bg-neutral-200'} transition-all duration-500 px-2 py-1 rounded-full `" @click="copyText(value)" >
            {{copied ? 'copiado' : 'copiar' }}
        </div>
    </div>
</template>

<script>

export default {
    props: {
        prefix: {
            type: String,
            required: true
        },
        value: {
            type: String,
            required: true
        },
    },
    data() {
        return {
            copied: false,
        };
    },
    methods: {
        copyText(text) {
            navigator.clipboard.writeText(text).then(() => {
                this.copied = true;
                setTimeout(() => {
                    this.copied = false;
                }, 2000);
            });
        }
    }
};
</script>