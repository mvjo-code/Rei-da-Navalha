<script setup>
defineProps({
  label: { type: String, required: true },
  valor: { type: String, required: true },
  href: { type: String, default: '' },
})
</script>

<template>
  <div class="campo">
    <span class="campo-label">{{ label }}</span>

    <component
      :is="href ? 'a' : 'span'"
      :href="href || undefined"
      class="campo-valor"
    >
      {{ valor }}
    </component>
  </div>
</template>

<style scoped>
.campo {
  display: flex;
  padding: 0.375rem 0.5rem;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.5rem;
  align-self: stretch;
  box-sizing: border-box;
  border-radius: 0.375rem;
  border: 1px solid rgba(212, 91, 14, 0.68);
}

.campo-label {
  color: rgba(207, 207, 207, 0.922);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.125rem;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 0.10125rem;
  text-transform: uppercase;
}

.campo-valor {
  display: flex;
  height: 2.1875rem;
  padding: 0 1.125rem;
  align-items: center;
  align-self: stretch;
  box-sizing: border-box;
  border-radius: 0.75rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
  background: rgba(0, 0, 0, 0.4);
  color: rgba(253, 253, 253, 0.891);
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.125rem;
  font-weight: 400;
  letter-spacing: 0.10125rem;
  text-transform: uppercase;
  text-decoration: none;
  transition:
    border-color 0.3s ease,
    color 0.3s ease;
}

/* só os valores que são link reagem ao mouse */
a.campo-valor:hover {
  border-color: rgba(212, 91, 14, 0.68);
  color: #fff;
  
}
</style>