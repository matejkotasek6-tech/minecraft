balíček com.matej;

import net.minecraft.block.Block;
import net.minecraft.block.material.Material;
import net.minecraft.item.BlockItem;
import net.minecraft.item.Položka;
import net.minecraft.item.ItemGroup;
import net.minecraftforge.event.RegistryEvent;
import net.minecraftforge.eventbus.api.SubscribeEvent;
import net.minecraftforge.fml.common.Mod;

@Mod("anetblock")
veřejná třída AnetBlockMod {

    // Definice bloku "anet"
    veřejný statický finální blok ANET_BLOCK = nový blok(Block.Properties
            .create(Materiál.HÁN)
            .tvrdostAodpor(2.0f, 6.0f)
            .setMapColor(net.minecraft.block.material.MaterialColor.BLUE)) // modrá barva
            .setRegistryName("anetblock", "anet");

    @Mod.EventBusSubscriber(bus = Mod.EventBusSubscriber.Bus.MOD)
    veřejná statická třída RegistryEvents {

        // Registrační blok
        @SubscribeEvent
        public static void onBlocksRegistry(final RegistryEvent.Register<Blok> událost) {
            událost.getRegistry().register(ANET_BLOCK);
        }

        // Registrace položky (aby se blok dal vzít do inventáře)
        @SubscribeEvent
        public static void onItemsRegistry(final RegistryEvent.Register<Položka> událost) {
            event.getRegistry().register(new BlockItem(ANET_BLOCK,
                    nový Item.Properties().group(ItemGroup.BUILDING_BLOCKS))
                    .setRegistryName("anetblock", "anet"));
        }
    }
}
