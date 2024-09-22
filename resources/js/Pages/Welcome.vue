<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
});

</script>

<template>
    <Head title="Welcome" />

    <main class="min-h-screen bg-slate-800 flex justify-center items-center">
        <div class="container mx-auto px-4 flex flex-col justify-center items-center">
            <img src="https://placehold.co/120" alt="Logo">

            <h1 class="text-2xl max-w-3xl text-white font-medium text-center mt-12 mb-8"><span class="font-extrabold">Request CRM</span> is a web application designed for system administration companies to efficiently register customers and manage service requests from clients.</h1>

            <nav v-if="canLogin" class="flex flex-col justify-center items-center gap-4">
                <Link
                    v-if="$page.props.auth.user"
                    :href="route('dashboard')"
                    class="text-white border-white border-2 rounded-lg py-2 px-4 text-xl"
                >
                    Dashboard
                </Link>

                <template v-else>
                    <Link
                        v-if="canRegister"
                        :href="route('register')"
                        class="text-white border-white border-2 rounded-lg py-2 px-4 text-xl"
                    >
                        Register
                    </Link>

                    <Link
                        :href="route('login')"
                        class="text-white text-lg underline"
                    >
                        Already registered?
                    </Link>
                </template>
            </nav>
        </div>
    </main>
</template>
