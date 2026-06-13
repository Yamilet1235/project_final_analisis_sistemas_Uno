<template>
    <section class="home">
        <h1 class="home__title">Sistema Hospitalario Integrado</h1>
        <p class="home__subtitle">Módulo 32: Validaciones de formularios.</p>

        <form class="form">
            <h2>Formulario de registro de paciente</h2>

            <label>Nombre completo</label>
            <input type="text" placeholder="Ej. María López">

            <label>Correo electrónico</label>
            <input type="email" placeholder="correo@ejemplo.com">

            <label>Teléfono</label>
            <input type="text" placeholder="Ej. 55554444">

            <button type="button">Validar formulario</button>
        </form>
    </section>
</template>

<script setup>
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

label {
    font-weight: 600;
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
</style>