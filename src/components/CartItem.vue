<script setup>
    
    defineProps({
        item: {
            type: Object,
            required: true,
            // se espera: { id, name, description, price, quantity, image }
        }
    })

    defineEmits(['increment', 'decrement', 'remove'])

    function formatPrice(value) {
        return new Intl.NumberFormat('es-ES', {
            style: 'currency',
            currency: 'EUR'
        }).format(value)
    }

</script>

<template>
    <article class="cart-item">
        <img
            :src="item.image"
            :alt="item.name"
            class="cart-item_img"/>

        <div class="cart-item_body">
            <div class="cart-item_top">
                <h2>{{ item.name }}</h2>
                <button
                    class="cart-item_remove"
                    type="button"
                    :aria-label="`Quitar ${item.name} de la cesta`"
                    @click="$emit('remove', item.id)"
                >
                    x
                </button>
            </div>

            <p class="cart-item_desc">{{ item.description }}</p>

            <div class="cart-item_bottom">
                <span class="cart-item_price">{{ formatPrice(item.price) }}</span>

                <div class="qty-control">
                    <button
                        type="button"
                        class="qty-control_btn"
                        :disabled="item.quantity <= 1"
                        :aria-label="`Reducir cantidad de ${item.name}`"
                        @click="$emit('decrement', item.id)"
                    >
                        -
                    </button>
                    <span class="qty-control_value">{{ item.quantity }}</span>
                    <button
                        type="button"
                        class="qty-control_btn"
                        :aria-label="`Aumentar cantidad de ${item.name}`"
                        @click="$emit('increment', item.id)"
                    >
                        +
                    </button>
                </div>
            </div>
        </div>
    </article>
</template>

<style scoped>
@reference '../src/main.css';

.cart-item {
    @apply
    flex flex-col gap-4
    rounded-lg border border-border-default
    bg-bg-container p-4 sm:flex-row
}

</style>