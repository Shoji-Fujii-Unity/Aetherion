# AETHERION ― 天空回廊 ― / Aetherion: Sky Corridor

<p align="center">
  <img alt="Three.js" src="https://img.shields.io/badge/Three.js-WebGL-black?logo=threedotjs&logoColor=white">
  <img alt="No build step" src="https://img.shields.io/badge/build_step-none-brightgreen">
  <img alt="Offline capable" src="https://img.shields.io/badge/offline-yes%20(after%20first%20load)-blue">
  <img alt="Languages" src="https://img.shields.io/badge/languages-5-ffb03a">
  <img alt="Save" src="https://img.shields.io/badge/save-localStorage-yellow">
  <img alt="Mobile" src="https://img.shields.io/badge/mobile-landscape%20ready-5fe3c0">
</p>

**AETHERION ― 天空回廊 ―** is a low‑poly 3D action platformer that runs entirely in a browser. Reach the goal gate at the end of a floating corridor, cut down eight monster species, grab eleven kinds of items, and clear twelve themed stages. It plays on a PC keyboard or a phone in landscape.

**Languages / 対応言語**

- [English](#english)
- [日本語](#日本語)
- [中文](#中文)
- [Español](#español)
- [Français](#français)

---

## At a glance

| Item | Value |
| --- | --- |
| Engine | Three.js (WebGL) |
| File | Single HTML file, no build step |
| View | Landscape first (phones show a rotate hint in portrait) |
| Languages | Japanese, English, Chinese, Spanish, French |
| Audio | Synthesised SFX + procedural music, global **ON / OFF** |
| Save | Browser **localStorage**, per stage best time, no cloud |
| Stages | 12 (4 and 12 are boss stages) |
| Monsters | 8 species |
| Items | 11 types |
| Input | Keyboard + mouse, touch (virtual stick + 3 buttons) |

---

## English

### How to run

1. Save the project as `index.html`.
2. Open the file in a modern desktop or mobile browser. The game needs **WebGL 1**.
3. On the first load an internet connection is required for the Three.js library (from unpkg) and the UI fonts (from Google Fonts). After that it plays offline.
4. If a browser blocks fonts or modules when opened from disk, host the file from any static web server or local preview, then open the served address.

Tap **TAP TO START** on the title screen to unlock audio (browser policy), then choose a mode.

### Game flow

- Run from the glowing **start portal** to the red **goal gate**.
- The goal is sealed on some stages. Collect the **Seal Key** to open it.
- Falling does not end the run: you lose **1 HP** and return to the last **checkpoint**.
- Stomping an enemy from above damages it. A melee strike or dash also hits enemies, and **Star of Zero** burns everything you touch.
- Every stage time is saved as your personal best. Clearing one unlocks the next.

### Controls

| Action | PC | Touch |
| --- | --- | --- |
| Move | `WASD` or arrow keys | Drag the **left half** of the screen |
| Camera | `Q` / `E`, or drag the right half | Drag the **right half** of the screen |
| Jump / double jump | `SPACE` | Button **B** |
| Attack | `J` or left mouse click | Button **A** |
| Dash | `K` or `SHIFT` | Button **C** |
| Pause | `ESC` or `P` | Pause icon on the top right |
| Toggle sound | `M` | Sound icon on the top right |

The touch pad only appears on touch devices. On a phone, turn the device **landscape**; portrait mode shows a rotate message instead of the game.

### Controls, camera, and the ground

- Move direction is relative to the camera; the camera slowly recentres to the corridor so running forward is always the screen's depth axis.
- Jump and double jump work over gaps. Jump pads and moving platforms change your route.
- The shadow under the hero marks the exact landing point.
- A dash gives brief invulnerability and a short speed burst; its cooldown shows on the button.

### Monsters (8)

| Species | Behaviour |
| --- | --- |
| Bounce Slime | Hops toward you in the corridor direction |
| Will‑o‑Wisp | Floats, weaves, then dives |
| Boulder Brute | Slow walker, heavy contact damage |
| Spore Maw | Stationary, lobs toxic clouds in arcs |
| Razor Hound | Locks on and charges in a straight line |
| Spiked Obelisk | Never moves, fires rings of thorns |
| Bomb Grub | Rushes you, flashes, detonates |
| Void Titan | Boss with slam, magic volley, and dash |

### Items (11)

- **Gem** — score
- **Drop of Life** — +1 HP
- **Heart Crystal** — +1 max HP
- **Ward Orb** — 8 s immunity to contact damage
- **Gale Feather** — +45 % speed for 10 s
- **Lodestone** — vacuums gems for 10 s
- **Sky Feather** — double jump for the rest of the stage
- **Brute Sigil** — double damage for 10 s
- **Star of Zero** — 6 s invincible, burns nearby enemies
- **Sands of Hours** — enemies move slower for 6 s
- **Seal Key** — opens a sealed gate

### Hazards

Spike beds, rotating saw blades with spikes on both ends, crumbling platforms that fall a moment after you step on them, and moving platforms that carry you.

### Audio and languages

- Sound is generated at runtime (no audio files). **ON / OFF** can be toggled from the title, pause, or the in‑game sound icon. State is saved.
- Language switches instantly from the title bar (**JA / EN / ZH / ES / FR**) and is saved. Stage names, the monster and item codex, and the help page are all translated.

### Save data

Progress lives in browser **localStorage** under the key `aetherion_save_v1`: unlocked stage, per‑stage best times, clear flags, total kills, language, sound, and quality.

- There is **no cloud save**. Clearing browser site data wipes progress.
- A new game overwrites only stage records and unlock state.
- The game stores no personal data and talks to no server.

### Performance and accessibility

- Auto fallback lowers pixel ratio and disables shadows on weaker touch devices. Quality can also be forced to HIGH / LOW from the title.
- Reduced motion is respected: ambient animation and UI transitions are minimised when the system asks for it.
- Camera pitch, dash invulnerability, checkpoints, and forgiving fall rules keep the run flowing.

### Tech notes

- Geometry is static‑merged per stage to keep draw calls low; particles share one instanced batch; shadows are one directional light only.
- Stage layout, enemy placement, gems, and items are seeded so every stage looks identical between plays, while audio and UI stay responsive.
- No bundler, no dependencies in the file itself beyond the Three.js CDN import.

---

## 日本語

### 遊び方 / 起動方法

1. プロジェクトを `index.html` として保存します。
2. 対応ブラウザ（WebGL 1 以上）で開いてください。
3. 初回は Three.js とフォントをネットから読み込むため通信が必要です。読み込み後はオフラインでも動きます。
4. ファイルを直接開いて表示が崩れる場合は、任意の静的サーバーで配信してからアクセスしてください。

タイトルで **タップして開始** を押すと音が出ます（ブラウザの仕様）。

### ゲームの流れ

- 光る **スタートの門** から、赤い **ゴール門** まで進みます。
- 一部のステージは門が封印されており、**封鍵の鍵** で開けられます。
- 落ちても即死ではありません。**HP が 1 減り**、チェックポイントに戻ります。
- 上から踏んでも攻撃できます。近接攻撃やダッシュでも攻撃でき、**無敵の星** は触れた敵を焼きます。
- タイムはステージごとにベストが保存され、クリアで次が解禁されます。

### 操作

| 動作 | PC | スマホ（タッチ） |
| --- | --- | --- |
| 移動 | `WASD` / 矢印キー | 画面**左半分**をドラッグ |
| 視点 | `Q` / `E`、または右半分ドラッグ | 画面**右半分**をドラッグ |
| ジャンプ / 二段跳 | `SPACE` | ボタン **B** |
| 攻撃 | `J` / 左クリック | ボタン **A** |
| ダッシュ | `K` / `SHIFT` | ボタン **C** |
| ポーズ | `ESC` / `P` | 右上のポーズボタン |
| サウンド切替 | `M` | 右上の音ボタン |

仮想ボタンはタッチ端末でだけ表示されます。スマホは **横画面** で遊んでください。縦画面では回転を促す案内が出ます。

### カメラと足場

- 視点は回廊方向へゆっくり自動追従するため、画面の奥が進行方向になります。
- ギャップは二段ジャンプで越えられます。ジャンプ台と移動床がルートを広げます。
- 足元の影が着地位置の目安です。
- ダッシュ中は短い無敵時間があります。クールタイムはボタンに反映されます。

### モンスター（8 種）

| 種類 | 特徴 |
| --- | --- |
| 跳ね泥 | 進行方向へ跳ねながら突進 |
| 燐火 | 宙を舞い、波を描いて急降下 |
| 岩塊獣 | 鈍重だが接触ダメージが重い |
| 胞子獣 | その場で毒胞子を弧軌道で撃つ |
| 鋭狼 | 直線突撃を仕掛ける |
| 尖塔 | 動かず全方位へ棘を放射 |
| 爆弾虫 | 近づいて点滅し、爆発 |
| 虚空の巨神 | 叩きつけ／弾幕／突進のボス |

### アイテム（11 種）

- **ジェム** — スコア
- **命の雫** — HP +1
- **心臓の結晶** — 最大 HP +1
- **shield の珠** — 8 秒接触ダメージ無効
- **疾風の羽** — 10 秒移動速度上昇
- **磁石石** — 10 秒ジェムを引き寄せる
- **翔羽** — そのステージの間、二段ジャンプ
- **剛力の護符** — 10 秒攻撃力 2 倍
- **無敵の星** — 6 秒無敵＋接触で敵にダメージ
- **時の砂** — 6 秒敵の動きが遅くなる
- **封鍵の鍵** — 封印された門を開ける

### ギミック

トゲ／両端に棘のある回転ノコギリ／踏むと一瞬で崩れる床／プレイヤーを運ぶ移動床。

### サウンドと言語

- 効果音・BGM はすべて合成音です（音声ファイルなし）。タイトル・ポーズ・右上ボタンで **ON / OFF** を切り替えられ、状態は保存されます。
- 言語はタイトル下部で **JA / EN / ZH / ES / FR** に即時切替（保存あり）。ステージ名・図鑑・ヘルプも翻訳されます。

### セーブデータ

進捗はブラウザの **localStorage**（キー `aetherion_save_v1`）に保存されます。解禁ステージ、各ステージのベストタイム、クリアフラグ、撃破数、言語、音量、画質です。

- **クラウド保存はありません**。ブラウザのサイトデータを消すとリセットされます。
- 新規ゲームはステージ記録と解禁状態を上書きします。
- 個人情報は保存せず、外部サーバーにも送信しません。

### 動作設定

- 弱いタッチ端末では自動で画質を下げます（ピクセル比率・影）。タイトルで HIGH / LOW を手動指定もできます。
- システムの「視差効果を減らす」設定に追従し、UI の動きを最小限にします。

### 技術メモ

- ステージごとに静的メッシュを合成して描画負荷を抑え、パーティクルはインスタンス描画、影はディレクショナルライト 1 灯のみ。
- ステージ構造はシード値で毎回同じ配置。ファイル内依存は CDN の Three.js だけで、ビルドは不要。

---

## 中文

### 运行方式

1. 将项目保存为 `index.html`。
2. 用支持 WebGL 1 的桌面或手机浏览器打开。
3. 首次加载需要联网获取 Three.js 与界面字体，之后可离线游玩。
4. 若从本地文件打开显示异常，请用任意静态服务器部署后访问。

标题界面点击 **点击开始** 以启用声音（浏览器限制）。

### 玩法

- 从发光的起点门跑到红色终点门。
- 部分关卡终点门被封印，需拾取 **封印之键** 开启。
- 坠落不会直接失败：扣除 **1 点 HP** 并回到检查点。
- 从上方踩踏也能攻击敌人；近战与冲刺均可造成伤害，**无敌之星** 接触即灼伤敌人。
- 系统自动记录每关最佳时间，通关后解锁下一关。

### 操作

| 动作 | PC | 触屏 |
| --- | --- | --- |
| 移动 | `WASD` / 方向键 | 拖拽画面 **左半区** |
| 视角 | `Q` / `E` 或拖拽右半区 | 拖拽画面 **右半区** |
| 跳跃 / 二段跳 | `SPACE` | 按钮 **B** |
| 攻击 | `J` / 左键 | 按钮 **A** |
| 冲刺 | `K` / `SHIFT` | 按钮 **C** |
| 暂停 | `ESC` / `P` | 右上角暂停按钮 |
| 声音开关 | `M` | 右上角声音按钮 |

虚拟按钮仅在触屏设备显示。手机请 **横屏** 游戏；竖屏时会提示旋转设备。

### 怪物（8 种）

跳泥怪（蹦跳突进）、磷火（俯冲）、岩块兽（高伤害）、孢子兽（抛射毒孢子）、锐狼（直线冲锋）、尖塔（全向放刺）、炸弹虫（靠近爆炸）、虚空巨神（叩击／弹幕／冲刺 Boss）。

### 道具（11 种）

宝石、命之滴（HP+1）、心脏水晶（最大 HP+1）、护盾珠、疾风之羽、磁石、翔羽（本关二段跳）、刚力护符（攻击翻倍）、无敌之星、时间之砂（减速）、封印之键。

### 陷阱

尖刺、带刺旋转锯、踩上后崩塌的地板、移动平台。

### 声音与语言

音效与音乐均为实时合成，无音频文件，可随时 **ON / OFF** 并保存。语言可在标题栏 **JA / EN / ZH / ES / FR** 即时切换，关卡名、图鉴、说明均已翻译。

### 存档

进度保存在浏览器 **localStorage**（键 `aetherion_save_v1`）：解锁进度、每关最佳时间、通关标记、击破数、语言、音量、画质。无云存档；清除浏览器数据会清空进度；不收集也不上传个人信息。

### 性能与技术

弱设备自动降低像素比并关闭阴影，也可在标题手动选择 HIGH / LOW。舞台几何合并、粒子实例化、单向光阴影；种子化关卡，无需构建步骤。

---

## Español

### Cómo jugar / ejecución

1. Guarda el proyecto como `index.html`.
2. Ábrelo en un navegador moderno con **WebGL 1** (escritorio o móvil).
3. La primera carga necesita internet para Three.js y las tipografías; después funciona sin conexión.
4. Si al abrir el archivo local algo falla, sírvelo desde cualquier servidor estático y abre la dirección servida.

Pulsa **TAP TO START** para activar el audio (política del navegador).

### Cómo se juega

- Corre desde el portal inicial hasta la puerta final roja.
- En algunos niveles la puerta está sellada: usa la **Llave de Sellado**.
- Caer no termina la partida: pierdes **1 PV** y vuelves al punto de control.
- Pisar a un enemigo desde arriba también daña. Estrella y ataque también golpean, y **Estrella Cero** quema a quien te toca.
- El tiempo por nivel se guarda como récord; al completar uno se desbloquea el siguiente.

### Controles

| Acción | PC | Táctil |
| --- | --- | --- |
| Mover | `WASD` o flechas | Arrastra la **mitad izquierda** |
| Cámara | `Q` / `E` o arrastrar a la derecha | Arrastra la **mitad derecha** |
| Saltar / doble salto | `ESPACIO` | Botón **B** |
| Atacar | `J` o clic izquierdo | Botón **A** |
| Dash | `K` o `SHIFT` | Botón **C** |
| Pausa | `ESC` o `P` | Icono de pausa arriba a la derecha |
| Sonido | `M` | Icono de sonido arriba a la derecha |

La pantalla táctil solo aparece en dispositivos de pulso. En móvil usa **modo horizontal**; en vertical verás un aviso para girar el dispositivo.

### Monstruos (8)

Lodo Saltarín, Feu Follet, Bruto de Roca, Faucespora, Sabueso Afilado, Obelisco, Larva Bomba y Titán del Vacío (jefe con golpe, ráfaga y carga).

### Objetos (11)

Gema, Gota de Vida, Cristal Cardíaco, Orbe de Escudo, Pluma Veloz, Magnetita, Pluma Celeste, Sigil Brutal, Estrella Cero, Arena del Tiempo y Llave de Sellado.

### Peligros

Pinchos, sierras giratorias con púas, plataformas que se desmoronan y plataformas móviles.

### Audio e idiomas

El audio es sintetizado (sin archivos). Puedes activar o silenciar **ON / OFF** desde el título, la pausa o el icono de sonido; el estado se guarda. El idioma cambia al instante en **JA / EN / ZH / ES / FR** y se memoriza.

### Datos guardados

El progreso vive en **localStorage** del navegador, clave `aetherion_save_v1`: niveles desbloqueados, mejores tiempos, marcas de completado, bajas, idioma, volumen y calidad. No hay nube: borrar datos del navegador reinicia el juego. No se guardan datos personales ni se envían a servidores.

### Rendimiento y técnica

En dispositivos táctiles débiles baja la resolución y apaga las sombras automáticamente, con opción forzada HIGH / LOW. Geometría unificada por nivel, partículas en lote instanciado, una sola luz con sombras, niveles por semilla y sin pasos de compilación.

---

## Français

### Lancer le jeu

1. Enregistre le projet sous `index.html`.
2. Ouvre‑le dans un navigateur compatible **WebGL 1**, sur ordinateur ou téléphone.
3. La première ouverture demande une connexion pour Three.js et les polices ; ensuite le jeu fonctionne hors ligne.
4. Si l'ouverture directe pose problème, sers le fichier avec n'importe quel serveur statique et ouvre l'adresse obtenue.

Touche **TOUCHEZ POUR COMMENCER** pour activer le son (règle du navigateur).

### But

- Va du portail lumineux de départ à la porte finale rouge.
- Sur certains niveaux la porte est scellée : utilise la **Clé de Sceau**.
- Tomber ne termine pas la partie : tu perds **1 PV** et reviens au point de contrôle.
- Écraser un ennemi de haut en bas fonctionne aussi. Dash et attaque frappent également, et l'**Étoile Zéro** brûle les ennemis au contact.
- Le temps par niveau est enregistré comme record ; finir un niveau débloque le suivant.

### Commandes

| Action | PC | Tactile |
| --- | --- | --- |
| Se déplacer | `WASD` ou flèches | Glisse sur la **moitié gauche** |
| Caméra | `Q` / `E` ou glisser à droite | Glisse sur la **moitié droite** |
| Saut / double saut | `ESPACE` | Bouton **B** |
| Attaquer | `J` ou clic gauche | Bouton **A** |
| Dash | `K` ou `SHIFT` | Bouton **C** |
| Pause | `ÉCHAP` ou `P` | Icône de pause en haut à droite |
| Son | `M` | Icône son en haut à droite |

Le pavé tactile n'apparaît que sur écran tactile. Sur téléphone, passe en **mode paysage** ; en portrait un message demande de pivoter l'appareil.

### Monstres (8)

Boue Bondissante, Feu Follet, Brute de Pierre, Gueule Sporique, Chien Aiguisé, Obélisque, Larve‑Bombe et le Titán du Vide (boss : slam, salve, charge).

### Objets (11)

Gemme, Goutte de Vie, Cristal Cardiaque, Orbe de Garde, Plume de Gale, Magnétite, Plume Céleste, Sigil Brutal, Étoile Zéro, Sable des Heures, Clé de Sceau.

### Dangers

Pics, scies tournantes à pointes, plateformes qui s'effondrent, plateformes mobiles.

### Audio et langues

Son entièrement synthétisé, sans fichier. Activation/silence **ON / OFF** depuis le titre, la pause ou l'icône son ; l'état est mémorisé. La langue bascule immédiatement en **JA / EN / ZH / ES / FR** et est sauvegardée.

### Sauvegarde

Le progrès est stocké dans **localStorage** du navigateur, clé `aetherion_save_v1` : niveaux débloqués, meilleurs temps, complétions, éliminations, langue, volume, qualité. Pas de cloud ; effacer les données du navigateur remet le jeu à zéro. Aucune donnée personnelle n'est stockée ni envoyée.

### Performance et technique

Les appareils tactiles faibles réduisent la résolution et coupent les ombres automatiquement, avec choix manuel HIGH / LOW. Géométrie fusionnée par niveau, particules en lot instancié, une seule lumière à ombres, niveaux déterministes et aucune étape de compilation.

---

## License

Provided as a showcase of browser‑based 3D. Free to study, modify, and adapt for your own projects. Attribution appreciated, not required.