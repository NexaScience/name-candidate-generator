# name-candidate-generator

AI/テック系のサービス名・プロダクト名・ブランド名の**候補を多数生成する** Claude Code スキル（生成専用）。

「ありそうでない造語」「実在語の転用」「2語の合成」「未開拓言語」など複数の戦略で、
**読みやすく・音が美しく・既存名と被らない**候補を生成し、読みカナ付きの構造化リストで返す。

## 特徴 / 方針
- **一発で読める・音が美しい**を死守（難読・無骨はNG）。
- **飽和ゾーンを避ける**（AI命名空間は猛烈に混雑。短い綺麗な造語はほぼ取られている）。
- **近い音=除外（厳格・基準を緩めない）**: 語頭・語幹・リズムが近い既存AIサービスが1つでもあれば外す
  （例: `velder`→`velerin` / `Reedmere`→`Reed.ai` / `Bolsena`→`Bolna` はNG）。"やや近い(△)"も通さない。
- **生成時の軽い自己フィルタ**: ①素の検索 ②`"<候補>" AI` ③近綴り/同音の音被り。
- 生成で完結し、**空き調査(商標/ドメイン/SNS)はしない**（別スキル `brand-name-availability` の役割）。
- 順序: 生成 → 自動調査(別スキル) → 生き残りだけ人間に提示 → 人間が選ぶ（手戻り防止）。

## 使い方
`SKILL.md` を Claude Code のスキルとして配置（例: `~/.claude/skills/name-candidate-generator/SKILL.md`）。
「名前を考えて/出して」等で起動する。

## 関連
- 調査スキル: [brand-name-availability](https://github.com/NexaScience/brand-name-availability)
