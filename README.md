# Arms Exchange

A real-time, top-down multiplayer battle royale that runs in the browser. Up to 50 players per match: friends join from their own devices with a 4-letter room code, and bots fill the rest. The whole game is a single `index.html` file with no server to set up.

**Play now:** https://hongruili5j.github.io/arms-exchange/

## How to play with friends

1. One person opens the link, enters a name and clicks **Create room**. A 4-letter room code appears.
2. Everyone else opens the same link, types the code under **Join** and clicks **Join**.
3. In the lobby, pick the same **Team** number as your friends if you want to play together (Solo means you are on your own). The host can add bots with the **+** button, then clicks **Start game**.
4. The host's browser tab runs the match for everyone, so the host should keep that tab open and in front.

You can also click **Practice vs bots** to play alone.

## Rules

- **Goal:** be the last player (or team) alive.
- **Start:** you begin with a pistol, a little ammo and **$0**.
- **Everything costs cash.** Collect coins on the ground, then press the pickup key next to a weapon, ammo, medkit or vest to buy it. Prices move over time and one weapon at a time gets a temporary damage boost.
- **Loot bags:** a defeated player drops a free bag with their gear. Open it to take items with the mouse.
- **Zone:** a shrinking safe zone damages anyone outside it, harder with every phase. It also hurts more inside buildings.
- **Airdrop:** after about 2.5 minutes a crate lands with powerful gold weapons.
- **Teams:** teammates spawn together and cannot hurt each other. A downed teammate can be revived by standing next to them and holding the pickup key for 3 seconds. If your whole team is down, you are out.
- **Spectate:** after you are eliminated you can watch your teammates.

## Controls

| Action | Default key |
| --- | --- |
| Move | W A S D |
| Aim / fire | Mouse / hold click |
| Pick up / revive / open bag | E |
| Drop | Q |
| Reload | R |
| Heal | F |
| Swap weapon | Tab (or 1 / 2) |
| Music on/off | M |

Click the keyboard button at the bottom left to rebind any key. On a phone, the left stick moves and the right stick aims and fires.

## How it works

- **No backend.** Players connect directly to each other with WebRTC through [PeerJS](https://peerjs.com/). The host's browser runs the authoritative game simulation at a fixed 30 ticks per second and sends state snapshots to the other players about 20 times per second. Other players send their inputs to the host.
- **Maps** are generated from a shared random seed, so every device builds the same terrain without sending the map over the network.
- **Fair vision:** the host only sends each player what they could see, including line of sight through doors, so players cannot see through walls.
- **Smoother play:** the player's own movement is predicted locally, and old network updates are dropped instead of queued.
- **Sound** (music and effects) is synthesized in the browser with the Web Audio API, so there are no audio files.
- Built with plain HTML, CSS, JavaScript and the Canvas API.

## Limitations

- Connections depend on the network. Some school or office Wi‑Fi blocks peer-to-peer traffic; mobile data or a hotspot usually works.
- The host's device does all the game logic, so a slow host affects everyone, and if the host closes the tab the match ends.
- Not tested with a large number of real devices at once.

## Ideas for next steps

- Ranked matches and persistent stats
- More maps and weapons
- Better mobile controls
- A relay server so connections work on stricter networks

## Credits

Designed and tested by Hongrui Li, built with help from Claude (Anthropic).
