<template>
    <div class="min-h-full flex flex-col">
        <Popover as="header" class="pb-24 bg-indigo-600" v-slot="{ open }">
            <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:max-w-7xl lg:px-8">
                <div class="relative py-5 flex items-center justify-center lg:justify-between">
                    <!-- Logo -->
                    <div class="absolute left-0 flex-shrink-0 lg:static">
                        <a href="#">
                            <span class="text-white text-lg uppercase font-semibold">VOTING POKER</span>
                        </a>
                    </div>

                    <!-- Settings Dropdown -->
                    <div class="ml-3 relative">
                        <BreezeDropdown align="right" width="48">
                            <template #trigger>
                                        <span class="inline-flex rounded-md">
                                            <button type="button"
                                                    class="inline-flex items-center px-3 py-2 leading-4 font-semibold text-gray-50 hover:text-white focus:outline-none transition ease-in-out duration-150">
                                                {{ $page.props.auth.user.name }}

                                                <svg class="ml-2 -mr-0.5 h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
                                                    <path fill-rule="evenodd"
                                                          d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                                                          clip-rule="evenodd"/>
                                                </svg>
                                            </button>
                                        </span>
                            </template>

                            <template #content>
                                <BreezeDropdownLink :href="route('logout')" method="post" as="button">
                                    Log Out
                                </BreezeDropdownLink>
                            </template>
                        </BreezeDropdown>
                    </div>

                </div>
                <div class="hidden lg:block border-t border-white border-opacity-20 py-5">
                    <div class="grid grid-cols-3 gap-8 items-center">
                        <div class="col-span-2 text-white font-semibold">
                            Your Space
                        </div>
                        <div>
                            <div class="max-w-md w-full mx-auto text-white font-semibold">
                                Management
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </Popover>

        <main class="-mt-24 pb-8 flex-1 flex flex-col items-center">

            <div class="w-full flex flex-1 px-4 sm:px-6 lg:max-w-7xl lg:px-8">
                <!-- Main 3 column grid -->
                <div class="w-full mx-auto grid grid-cols-1 gap-4 lg:grid-cols-3 lg:gap-8">

                    <!-- Left column -->
                    <div class="grid grid-cols-1 gap-4 lg:col-span-2">
                        <section aria-labelledby="section-1-title">
                            <div class="h-full rounded-lg bg-white overflow-hidden shadow">
                                <div class="p-6 flex-1">
                                    <slot name="main"></slot>
                                </div>
                            </div>
                        </section>
                    </div>

                    <!-- Right column -->
                    <div class="grid grid-cols-1 gap-4">
                        <section aria-labelledby="section-2-title">
                            <h2 class="sr-only" id="section-2-title">Section title</h2>
                            <div class="rounded-lg bg-white overflow-hidden shadow">
                                <div class="p-6">
                                    <slot name="sidebar"></slot>
                                </div>
                            </div>
                        </section>
                    </div>

                </div>
            </div>
        </main>

        <footer>
            <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8 lg:max-w-7xl">
                <div class="border-t border-gray-200 py-8 text-sm text-gray-500 text-center sm:text-left"><span class="block sm:inline">&copy; 2021 Tailwind Labs Inc.</span>
                    <span class="block sm:inline">All rights reserved.</span></div>
            </div>
        </footer>
    </div>
</template>

<script>
import {
    Menu,
    MenuButton,
    MenuItem,
    MenuItems,
    Popover,
    PopoverButton,
    PopoverOverlay,
    PopoverPanel,
    TransitionChild,
    TransitionRoot,
} from '@headlessui/vue';
import { BellIcon, MenuIcon, XIcon } from '@heroicons/vue/outline';
import { SearchIcon } from '@heroicons/vue/solid';
import BreezeApplicationLogo from '@/Components/ApplicationLogo.vue';
import BreezeDropdown from '@/Components/Dropdown.vue';
import BreezeDropdownLink from '@/Components/DropdownLink.vue';
import BreezeNavLink from '@/Components/NavLink.vue';
import BreezeResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';

const user = {
    name: 'Tom Cook',
    email: 'tom@example.com',
    imageUrl:
        'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80',
};

const userNavigation = [
    {name: 'Your Profile', href: '#'},
    {name: 'Settings', href: '#'},
    {name: 'Sign out', href: '#'},
];

export default {
    components: {
        Menu,
        MenuButton,
        MenuItem,
        MenuItems,
        Popover,
        PopoverButton,
        PopoverOverlay,
        PopoverPanel,
        TransitionChild,
        TransitionRoot,
        BellIcon,
        MenuIcon,
        SearchIcon,
        XIcon,
        BreezeResponsiveNavLink,
        BreezeDropdown,
        BreezeApplicationLogo,
        BreezeDropdownLink,
        BreezeNavLink
    },
    setup() {
        return {
            user,
            userNavigation,
        };
    },
    data() {
        return {
            showingNavigationDropdown: false,
        };
    },
};
</script>
