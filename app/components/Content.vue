<template>
    <div class="grid grid-cols-2 h-full">
        <div class="flex flex-col p-5">
            <div
                class="flex justify-between items-center pb-5 border-b border-[#222]"
            >
                <p class="text-sm text-left font-semibold text-blue-500">CT</p>
                <p class="text-base text-left font-semibold">
                    {{ players.filter((player) => player.team == 0).length }}
                </p>
            </div>

            <div class="grid grid-cols-1 gap-2 mt-5 overflow-y-auto">
                <div
                    v-for="player in players.filter(
                        (player) => player.team == 0,
                    )"
                    class="grid grid-cols-2 items-center bg-[#1a1a1a] p-4 border border-[#222] rounded"
                >
                    <div class="flex flex-col gap-1 text-left">
                        <p class="text-sm font-semibold">{{ player.name }}</p>
                        <p class="text-xs text-[#666] uppercase">
                            {{ player.position }}
                        </p>
                    </div>

                    <div class="flex flex-col gap-1 text-right">
                        <p
                            :class="[
                                'text-sm font-semibold',
                                healthColor(player.health),
                            ]"
                        >
                            {{ player.health }}
                        </p>
                        <p class="text-xs text-[#666] uppercase">
                            {{ player.equipment }}
                        </p>
                        <p class="text-xs text-[#666] uppercase">
                            ${{ player.money }}
                        </p>
                    </div>
                </div>
            </div>
        </div>

        <div class="flex flex-col p-5">
            <div
                class="flex justify-between items-center pb-5 border-b border-[#222]"
            >
                <p class="text-sm text-left font-semibold text-red-500">T</p>
                <p class="text-base text-left font-semibold">
                    {{ players.filter((player) => player.team == 1).length }}
                </p>
            </div>

            <div class="grid grid-cols-1 gap-2 mt-5 overflow-y-auto">
                <div
                    v-for="player in players.filter(
                        (player) => player.team == 1,
                    )"
                    class="grid grid-cols-2 items-center bg-[#1a1a1a] p-4 border border-[#222] rounded"
                >
                    <div class="flex flex-col gap-1 text-left">
                        <p class="text-sm font-semibold">{{ player.name }}</p>
                        <p class="text-xs text-[#666] uppercase">
                            {{ player.position }}
                        </p>
                    </div>

                    <div class="flex flex-col gap-1 text-right">
                        <p
                            :class="[
                                'text-sm font-semibold',
                                healthColor(player.health),
                            ]"
                        >
                            {{ player.health }}
                        </p>
                        <p class="text-xs text-[#666] uppercase">
                            {{ player.equipment }}
                        </p>
                        <p class="text-xs text-[#666] uppercase">
                            ${{ player.money }}
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
interface Player {
    name: string;
    team: number;
    position: string;
    equipment: string;
    health: number;
    money: number;
}

const healthColor = (health: number) => {
    if (health > 70) return "text-green-500";
    if (health > 30) return "text-yellow-500";
    return "text-red-500";
};

const players: Player[] = [
    {
        name: "Player 1",
        team: 0,
        position: "Bombsite A",
        equipment: "M4A1-S",
        health: 100,
        money: 8500,
    },
    {
        name: "Player 2",
        team: 1,
        position: "Mid",
        equipment: "AK-47",
        health: 78,
        money: 6200,
    },
    {
        name: "Player 3",
        team: 0,
        position: "Bombsite B",
        equipment: "AWP",
        health: 45,
        money: 4750,
    },
    {
        name: "Player 4",
        team: 1,
        position: "Long A",
        equipment: "Desert Eagle",
        health: 23,
        money: 1200,
    },
    {
        name: "Player 5",
        team: 0,
        position: "Connector",
        equipment: "FAMAS",
        health: 89,
        money: 3200,
    },
    {
        name: "Player 6",
        team: 1,
        position: "Tunnels",
        equipment: "Galil AR",
        health: 100,
        money: 1900,
    },
];
</script>
