<template>
    <section class="home">
        <h1 class="home__title">Sistema Hospitalario Integrado</h1>
        <p class="home__subtitle">Módulo 32: Validaciones de formularios.</p>

        <form class="form" @submit.prevent="submitForm" novalidate>
            <h2>Formulario de registro de paciente</h2>

            <label>Nombre completo</label>
            <input v-model="form.nombre" type="text" placeholder="Ej. María López">
            <span v-if="errors.nombre" class="error">{{ errors.nombre }}</span>

            <label>Correo electrónico</label>
            <input v-model="form.email" type="email" placeholder="correo@ejemplo.com">
            <span v-if="errors.email" class="error">{{ errors.email }}</span>

            <label>Teléfono</label>
            <input v-model="form.telefono" type="text" placeholder="Ej. 55554444">
            <span v-if="errors.telefono" class="error">{{ errors.telefono }}</span>

            <button type="submit">Validar formulario</button>

            <p v-if="successMessage" class="success">{{ successMessage }}</p>
        </form>
    </section>
</template>

<script setup>
import { reactive, ref } from 'vue';

const form = reactive({
    nombre: '',
    email: '',
    telefono: '',
});

const errors = reactive({
    nombre: '',
    email: '',
    telefono: '',
});

const successMessage = ref('');

const submitForm = () => {
    errors.nombre = '';
    errors.email = '';
    errors.telefono = '';
    successMessage.value = '';

    if (!form.nombre.trim()) {
        errors.nombre = 'El nombre completo es obligatorio.';
    } else if (form.nombre.trim().length < 3) {
        errors.nombre = 'El nombre debe tener al menos 3 caracteres.';
    }

    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!form.email.trim()) {
        errors.email = 'El correo electrónico es obligatorio.';
    } else if (!emailRegex.test(form.email)) {
        errors.email = 'Ingrese un correo electrónico válido.';
    }

    const phoneRegex = /^[0-9]{8}$/;
    if (!form.telefono.trim()) {
        errors.telefono = 'El teléfono es obligatorio.';
    } else if (!phoneRegex.test(form.telefono)) {
        errors.telefono = 'El teléfono debe contener exactamente 8 dígitos.';
    }

    if (!errors.nombre && !errors.email && !errors.telefono) {
        successMessage.value = 'Formulario validado correctamente. Los datos están listos para enviarse.';
    }
};
</script>

<style scoped>
.home {
    max-width: 720px;
}

.home__title {
    font-size: 1.75rem;
    font-weight: 700;
    margin-bottom: 0.75rem;
}

.home__subtitle {
    color: #475569;
    line-height: 1.6;
    margin-bottom: 1.5rem;
}

.form {
    background: #ffffff;
    border: 1px solid #e5e7eb;
    border-radius: 12px;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
}

.form h2 {
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
}

input {
    border: 1px solid #cbd5e1;
    border-radius: 8px;
    padding: 0.65rem;
}

button {
    margin-top: 1rem;
    background: #2563eb;
    color: white;
    border: none;
    border-radius: 8px;
    padding: 0.75rem;
    cursor: pointer;
    font-weight: 600;
}

.error {
    color: #dc2626;
    font-size: 0.9rem;
}

.success {
    color: #15803d;
    font-weight: 600;
    margin-top: 0.75rem;
}
label {
    font-weight: 600;
}
</style>