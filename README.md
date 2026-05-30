# Froggies 🐸

**Froggies** is a Bitcoin-native pond collection designed for nat.fun, with a fixed supply of **4,032 unique Froggies**.

Both supply and trait generation are derived entirely from Bitcoin blockchain data, creating a collection that is deterministic, verifiable, and free from off-chain randomness.

---

## Supply Generation

Bitcoin adjusts mining difficulty every **2,016 blocks**, known as a *difficulty period*. Each block within a difficulty period shares the same compact difficulty value stored in the block header's `bits` field.

Froggies identifies difficulty periods whose `bits` value contains the **`fc` signal**. Across Bitcoin's history, this condition occurs in two qualifying difficulty periods:
| Generation | Block Range | First Block Date (UTC) | `bits` Value | Froggies |
|------------|-------------|------------------------|--------------|------------|
| Gen 1 | 266,112 – 268,127 | 2013-10-26 02:24:32 | `190afc85` | 2016 |
| Gen 2 | 933,408 – 935,423 | 2026-01-22 19:31:22 | `1701fca1` | 2016 |

Each qualifying difficulty period contains exactly **2,016 blocks**:

* Gen 1: 2,016 Froggies
* Gen 2: 2,016 Froggies

**Total Supply = 4,032 Froggies**

Every Froggie is permanently linked to one specific Bitcoin block from these qualifying periods.

---

## Trait Generation

Traits are generated directly from the assigned Bitcoin block hash.

For each Froggie:

1. The block hash is divided into deterministic roll values.
2. Each roll is mapped to rarity ranges.
3. The resulting values determine the Froggie's attributes.

Trait categories include:

* Body Color
* Eyes
* Expression
* Headgear
* Swamp Accessories
* Background / Aura

Because all trait rolls originate from Bitcoin block hashes, every Froggie can be independently verified and reproduced from on-chain data alone.

---

## Bitcoin-Native by Design

Froggies uses Bitcoin as the sole source of truth for:

* Collection supply
* Generation assignment
* Trait rarity
* Trait selection

No off-chain randomness, reveal process, or external entropy source is required.

The result is a fully deterministic collection whose existence and attributes are anchored directly to Bitcoin's blockchain history.

## Trait Generation

Each Froggie's traits are generated directly from its assigned Bitcoin block hash.

Bitcoin block hashes are already represented as 64-character hexadecimal strings:

```text
00000000000000000001dbe44ff50d592964c9414af0f08b3d3654e806983d15
```

The hash is divided into eight deterministic 8-character chunks:

```text
00000000 | 00000000 | 0001dbe4 | 4ff50d59
2964c941 | 4af0f08b | 3d3654e8 | 06983d15
```

Each chunk is a hexadecimal value using the character set:

```text
0 1 2 3 4 5 6 7 8 9 a b c d e f
```

The chunks are converted into integers and used as deterministic trait rolls.

### Example

```text
0001dbe4 → Body Color
4ff50d59 → Eyes
2964c941 → Mouth / Expression
4af0f08b → Headgear / Props
3d3654e8 → Swamp Accessory
06983d15 → Background / Aura
```

Each resulting number is mapped to a predefined rarity range within its trait category, producing the final Froggie.

```text
Bitcoin Block Hash
        ↓
Split into Hex Chunks
        ↓
Convert Chunks to Numbers
        ↓
Map Numbers to Trait Ranges
        ↓
Generate Froggie Traits
```

Because every trait originates from Bitcoin block data, the entire collection is deterministic, reproducible, and independently verifiable without any off-chain randomness.


| Category               | Traits                                                                                                                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Body Color**         | Swamp Green (701), Pastel Green (585), Toxic Yellow (496), Turquoise (468), Night Black (414), Neon Pink (394), Ghost (333), Albino White (262), Gold Body (201), Diamond Body (178) |
| **Eyes**               | Wide Sleepy (1,473), One-Eye Wink (904), Bulging (598), Hypnotic Spiral (397), Gold Eyes (291), Diamond Eyes (192), Laser Eyes (177)                                                 |
| **Mouth / Expression** | Grin (1,551), Croak (980), Deadpan (618), Shocked (413), Frog Tongue (290), Chewing Bug (180)                                                                                        |
| **Headgear / Props**   | None (893), Leaf Cap (769), Ribbit Hoodie (604), Bandana (399), Goggles (398), Wizard Hat (322), Pirate Hat (316), Pin Wheel Hat (169), Crown (162)                                  |
| **Swamp Accessories**  | Lily Pad (823), Fly (751), Bubble (698), Mushrooms (616), Lightning Bug (469), Bones (290), Fishing Hook (208), Coin Stack (177)                                                     |
| **Background / Aura**  | Sunrise Marsh (903), Murky Pond (857), Moonlit Swamp (783), Rainy Night (622), Toxic Swamp Mist (368), Bitcoin Orange Glow (306), Neon Vapor (193)                                   |
