
package com.matej;

import net.minecraft.block.Block;
import net.minecraft.block.material.Material;
import net.minecraft.item.BlockItem;
import net.minecraft.item.Item;
import net.minecraft.item.ItemGroup;
import net.minecraftforge.event.RegistryEvent;
import net.minecraftforge.eventbus.api.SubscribeEvent;
import net.minecraftforge.fml.common.Mod;

@Mod("anetblock")
public class AnetBlockMod {

    // Definice bloku "anet"
    public static final Block ANET_BLOCK = new Block(Block.Properties
            .create(Material.ROCK)
            .hardnessAndResistance(2.0f, 6.0f)
            .setMapColor(net.minecraft.block.material.MaterialColor.BLUE)) // modr� barva
            .setRegistryName("anetblock", "anet");

    @Mod.EventBusSubscriber(bus = Mod.EventBusSubscriber.Bus.MOD)
    public static class RegistryEvents {

        // Registrace bloku
        @SubscribeEvent
        public static void onBlocksRegistry(final RegistryEvent.Register<Block> event) {
            event.getRegistry().register(ANET_BLOCK);
        }

        // Registrace itemu (aby se blok dal vz�t do invent��e)
        @SubscribeEvent
        public static void onItemsRegistry(final RegistryEvent.Register<Item> event) {
            event.getRegistry().register(new BlockItem(ANET_BLOCK,
                    new Item.Properties().group(ItemGroup.BUILDING_BLOCKS))
                    .setRegistryName("anetblock", "anet"));
        }
    }
}
