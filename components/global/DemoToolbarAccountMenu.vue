<script setup lang="ts">
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { useAuthStore } from '~/views/auth/stores';

const authStore = useAuthStore()
const router = useRouter()
const logout = () => {
    localStorage.removeItem('accessToken')
    // router.push('/login')
}
</script>

<template>
    <div
        class="group relative z-20 inline-flex items-center justify-center text-end"
    >
        <Menu
            v-slot="{ close }"
            as="div"
            class="relative z-20 size-9 text-left"
        >
            <MenuButton as="template">
                <button
                    type="button"
                    class="group-hover:ring-primary-500 dark:ring-offset-muted-900 inline-flex size-9 items-center justify-center rounded-full ring-1 ring-transparent transition-all duration-300 group-hover:ring-offset-4"
                >
                    <div
                        class="relative inline-flex size-9 items-center justify-center rounded-full"
                    >
                        <img
                            src="/public/logo.png"
                            class="max-w-full rounded-full object-cover shadow-sm dark:border-transparent"
                            alt=""
                        />
                    </div>
                </button>
            </MenuButton>

            <Transition
                enter-active-class="transition duration-100 ease-out"
                enter-from-class="transform scale-95 opacity-0"
                enter-to-class="transform scale-100 opacity-100"
                leave-active-class="transition duration-75 ease-in"
                leave-from-class="transform scale-100 opacity-100"
                leave-to-class="transform scale-95 opacity-0"
            >
                <MenuItems
                    class="divide-muted-100 border-muted-200 dark:divide-muted-700 dark:border-muted-700 dark:bg-muted-800 absolute end-0 mt-2 w-64 origin-top-right divide-y rounded-md border bg-white shadow-lg focus:outline-none"
                >
                    <div class="p-6 text-center">
                        <div
                            class="relative mx-auto flex size-20 items-center justify-center rounded-full"
                        >
                            <img
                                src="/public/logo.png"
                                class="max-w-full rounded-full object-cover shadow-sm dark:border-transparent"
                                alt=""
                            />
                        </div>
                        <div class="mt-3">
                            <h6
                                class="font-heading text-muted-800 text-sm font-medium dark:text-muted-50"
                            >
                                {{ authStore.userData.fullName }}
                            </h6>
                            <p class="text-muted-200 mb-4 font-sans text-xs">
                                {{ authStore.userData.email }}
                            </p>
                            <BaseButton
                                to="/"
                                rounded="lg"
                                class="w-full"
                                @click.passive="close"
                            >
                                ادارة الحساب
                            </BaseButton>
                        </div>
                    </div>

                    <div class="p-6">
                        <BaseButton
                            rounded="lg"
                            class="w-full"
                            @click="logout"
                        >
                            تسجيل الخروج
                        </BaseButton>
                    </div>
                </MenuItems>
            </Transition>
        </Menu>
    </div>
</template>
