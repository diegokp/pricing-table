<script  setup lang="ts">
import { ref } from 'vue';
import PricingTab from "../components/pricingTab.vue";

const isAnnual = ref<boolean>(true)

</script>


<template>
    <div>
        <!-- Pricing toggle -->
        <div class="flex justify-center max-w-[14rem] m-auto mb-8 lg:mb-16">
            <div class="relative flex w-full p-1 bg-slate-500 rounded-full">
                <span class="absolute inset-0 m-1 pointer-events-none" aria-hidden="true">
                    <span class="absolute inset-0 w-1/2 bg-indigo-500 rounded-full shadow-sm shadow-indigo-950/10 transform transition-transform duration-150 ease-in-out" :class="isAnnual ? 'translate-x-0' : 'translate-x-full'"></span>
                </span>
                <button
                    class="relative flex-1 text-sm font-medium h-8 rounded-full focus-visible:outline-none focus-visible:ring focus-visible:ring-indigo-300 dark:focus-visible:ring-slate-600 transition-colors duration-150 ease-in-out"
                    :class="isAnnual ? 'text-white' : 'text-slate-500 dark:text-slate-400'"
                    @click="isAnnual = true"
                    :aria-pressed="isAnnual"
                >Anual</button>
                <button
                    class="relative flex-1 text-sm font-medium h-8 rounded-full focus-visible:outline-none focus-visible:ring focus-visible:ring-indigo-300 dark:focus-visible:ring-slate-600 transition-colors duration-150 ease-in-out"
                    :class="isAnnual ? 'text-slate-500 dark:text-slate-400' : 'text-white'"
                    @click="isAnnual = false"
                    :aria-pressed="isAnnual"
                >Mensual</button>
            </div>
        </div> 
        
        <div class="max-w-sm mx-auto grid gap-6 lg:grid-cols-3 items-start lg:max-w-none">
            <!-- Pricing tab 1 -->
            <PricingTab
                :yearly="isAnnual"
                planName="Personal"
                :price="{ yearly: '490€', monthly: 'Gratis' }"
                planDescription="Durante 1 mes. Luego 49€/mes*"
                planAnnualDescription="2 meses gratis por el pago adelantado."
                plan-period-year="/año"
                :features="[
                    '1 usuario',
                    'Importación datos clientes',
                    'Catálogo de 100 productos',
                    'Presupuestos',
                    'Albaranes',
                    'Facturas',
                    'Orden de trabajo',
                ]"
                button-text="¡Comienza hoy!"
            />
            <!-- Pricing tab 2 -->
            <PricingTab
                :yearly="isAnnual"
                :popular="true"
                planName="Pofesional"
                :price="{ yearly: '990€', monthly: '99€' }"
                planDescription="Antes por "
                discount="199€"
                planAnnualDescription="2 meses gratis por el pago adelantado."
                plan-period-month="/mes"
                plan-period-year="/año"
                :features="[
                    'Plan básico',
                    'Múltiples usuarios (hasta 3)',
                    'Configuración 5 máquinas',
                    'Proveedores',
                    'Recibos',
                    'Compras',
                    '5 horas de formación online',
                ]"
                button-text="Contratar"
            />
            <!-- Pricing tab 3 -->
            <PricingTab
                :yearly="isAnnual"
                planName="Empresa"
                planDescription="Sin limites!"
                planAnnualDescription="Sin limites!"
                :price="{ yearly: 'Consultar', monthly: 'Consultar' }"
                :features="[
                    'Usuarios ilimitados',
                    'Prodctos ilimitados',
                    'Solicitud de pedidos',
                    'CRM',
                    'Finanzas',
                    'Informes y estadísticas',
                    'Integraciones Apps',
                    'Formación personalizada',
                    'Módulos avanzados',
                ]"
                button-text="Contáctanos"
            />
        </div>
    </div>
</template>