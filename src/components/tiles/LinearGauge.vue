<template>
    <Tile title="線形ゲージ" v-slot="{palette}">
        <div class="line-gauge-tile">
            <div class="flex-row">
                <h4>売上: {{ wjFormat(data.items[data.items.length - 1].sales, 'c') }}</h4>
                <wj-linear-gauge
                        :value="data.items[data.items.length-1].sales"
                        :min="0"
                        :max="1500"
                        :thickness="0.15"
                        :thumbSize="9"
                >
                    <wj-range :wjProperty="'pointer'" :color="palette[0]"></wj-range>
                </wj-linear-gauge>
            </div>

            <div class="flex-row">
                <h4>費用: {{ wjFormat(data.items[data.items.length - 1].expenses, 'c') }}</h4>
                <wj-linear-gauge
                        :value="data.items[data.items.length-1].expenses"
                        :min="0"
                        :max="1500"
                        :thickness="0.15"
                        :thumbSize="9"
                        :pointer="{ color: palette[1] }"
                >
                    <wj-range :wjProperty="'pointer'" :color="palette[1]"></wj-range>
                </wj-linear-gauge>
            </div>

            <div class="flex-row">
                <h4>利益: {{ wjFormat(data.items[data.items.length - 1].profit, 'c') }}</h4>
                <wj-linear-gauge
                        :value="data.items[data.items.length-1].expenses"
                        :min="0"
                        :max="1500"
                        :thickness="0.15"
                        :thumbSize="9"
                        :pointer="{ color: palette[2] }"
                >
                    <wj-range :wjProperty="'pointer'" :color="palette[2]"></wj-range>
                </wj-linear-gauge>
            </div>

            <h3>{{ wjFormat(data.items[data.items.length - 1].date, 'Y') }}のKPI</h3>
        </div>
    </Tile>
</template>

<script>
    import Tile from './Tile.vue';
    import { wjFormat } from '@grapecity/wijmo.vue2.core';
    import { WjLinearGauge, WjRange } from '@grapecity/wijmo.vue2.gauge';
    import DataService from '../../services/data.service';

    export default {
        setup: () => ({
            data: DataService.getData(),
            wjFormat,
        }),
        components: {
            Tile,
            WjLinearGauge,
            WjRange,
        },
    }
</script>

<style scoped>
</style>