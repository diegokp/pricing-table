<script setup lang="ts">
interface Props {
    yearly: boolean
    popular?: boolean
    planName: string
    planPeriodMonth?: string
    planPeriodYear?: string
    discount?: string
    price: {
        monthly: string
        yearly: string
    }
    planDescription?: string
    planAnnualDescription?: string
    features: string[]
    buttonText: string
}

const props = defineProps<Props>()
</script>

<template>
    <div class="h-full" :class="{ 'dark': props.popular }">
        <div class="relative flex flex-col h-full p-6 rounded-lg border border-slate-200 ">
            <div v-if="props.popular" class="absolute top-0 right-0 mr-6 -mt-4">
                <div class="inline-flex items-center text-xs font-semibold py-1.5 px-3 bg-emerald-500 text-white rounded-full shadow-sm shadow-slate-950/5">Recomendado</div>
            </div>
            <div class="mb-5">
                <div class="text-slate-900 dark:text-slate-200 font-semibold mb-1">{{ props.planName }}</div>
                <div class="inline-flex items-baseline mb-2">
                    <span class="text-slate-900 dark:text-slate-200 font-bold text-4xl" v-text="yearly ? props.price.yearly : props.price.monthly"></span>
                </div>
                <span v-if="props.yearly" class="text-slate-500 font-medium">{{ planPeriodYear}}</span>
                <span v-else="!props.yearly" class="text-slate-500 font-medium">{{ planPeriodMonth }}</span>
                <div v-if="props.yearly" class="text-sm text-slate-500 mb-5">{{ props.planAnnualDescription  }}</div>
                <div v-else="!props.yearly" class="text-sm text-slate-500 mb-5">{{ props.planDescription }} <span class="line-through  text-white">{{ discount }}</span></div>
            </div>
            <ul class="text-slate-600 dark:text-slate-400 text-sm space-y-3 grow">
                <template v-for="feature in props.features">
                    <li class="flex items-center">
                        <svg class="w-3 h-3 fill-emerald-500 mr-3 shrink-0" viewBox="0 0 12 12" xmlns="http://www.w3.org/2000/svg">
                            <path d="M10.28 2.28L3.989 8.575 1.695 6.28A1 1 0 00.28 7.695l3 3a1 1 0 001.414 0l7-7A1 1 0 0010.28 2.28z" />
                        </svg>
                        <span>{{ feature }}</span>
                    </li>
                </template>
            </ul>
            <a v-if="props.yearly" class="w-full inline-flex mt-8 justify-center whitespace-nowrap rounded-md bg-indigo-500 px-3.5 py-2.5 text-sm font-medium text-white shadow-sm shadow-indigo-950/10 hover:bg-indigo-600 focus-visible:outline-none focus-visible:ring focus-visible:ring-indigo-300 dark:focus-visible:ring-slate-600 transition-colors duration-150" href="#0">
                    {{buttonText}}
            </a>
            <a v-else="!props.yearly" class="w-full inline-flex mt-8 justify-center whitespace-nowrap rounded-md bg-red-500 px-3.5 py-2.5 text-sm font-medium text-white shadow-sm shadow-indigo-950/10 hover:bg-indigo-600 focus-visible:outline-none focus-visible:ring focus-visible:ring-indigo-300 dark:focus-visible:ring-slate-600 transition-colors duration-150" href="#0">
                {{buttonText}}
            </a>
        </div>
    </div>
</template>