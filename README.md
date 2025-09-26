# love-system
MBTIと恋愛MBTIの融合！！
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>恋愛MBTIアンケート</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { font-family: 'Arial', sans-serif; background: #f5f5fa; color: #333; margin: 0; }
    .container { max-width: 500px; margin: 40px auto; background: #fff; padding: 24px 32px 32px; border-radius: 10px; box-shadow: 0 4px 16px rgba(0,0,0,0.07); }
    h1 { text-align: center; color: #ea4c89; }
    label { display: block; margin-top: 16px; font-weight: bold; }
    select { margin-top: 8px; width: 100%; padding: 8px; border-radius: 4px; border: 1px solid #ccc; font-size: 1em; }
    button { margin-top: 24px; background: #ea4c89; color: #fff; border: none; padding: 12px 0; width: 100%; border-radius: 6px; font-size: 1.1em; cursor: pointer; }
    .result-text { margin-top: 32px; background: #f7cfe3; padding: 16px; border-radius: 6px; color: #333; }
  </style>
</head>
<body>
  <div class="container">
    <h1>恋愛MBTIアンケート</h1>
    <form id="surveyForm">
      <label>あなたのMBTIタイプは？</label>
      <select name="mbti" required>
        <option value="">選択してください</option>
        <option value="INTJ">INTJ</option>
        <option value="INTP">INTP</option>
        <option value="ENTJ">ENTJ</option>
        <option value="ENTP">ENTP</option>
        <option value="INFJ">INFJ</option>
        <option value="INFP">INFP</option>
        <option value="ENFJ">ENFJ</option>
        <option value="ENFP">ENFP</option>
        <option value="ISTJ">ISTJ</option>
        <option value="ISFJ">ISFJ</option>
        <option value="ESTJ">ESTJ</option>
        <option value="ESFJ">ESFJ</option>
        <option value="ISTP">ISTP</option>
        <option value="ISFP">ISFP</option>
        <option value="ESTP">ESTP</option>
        <option value="ESFP">ESFP</option>
      </select>

      <label style="margin-top:24px;">あなたの恋愛傾向は？</label>
      <select name="loveType" required>
        <option value="">選択してください</option>
        <option value="LCRO">LCRO</option>
        <option value="LCRE">LCRE</option>
        <option value="LCPO">LCPO</option>
        <option value="LCPE">LCPE</option>
        <option value="LARO">LARO</option>
        <option value="LARE">LARE</option>
        <option value="LAPO">LAPO</option>
        <option value="LAPE">LAPE</option>
        <option value="FCRO">FCRO</option>
        <option value="FCRE">FCRE</option>
        <option value="FCEO">FCEO</option>
        <option value="FCPE">FCPE</option>
        <option value="FARO">FARO</option>
        <option value="FAPE">FAPE</option>
        <option value="FARE">FARE</option>
        <option value="FAPO">FAPO</option>
      </select>

      <button type="submit">送信する</button>
    </form>
    <div class="result-text" id="resultText" style="display:none;"></div>
  </div>
  <script>
    document.getElementById("surveyForm").addEventListener("submit", function(e){
      e.preventDefault();
      const mbti = this.mbti.value;
      const loveType = this.loveType.value;

      // 診断文生成
      const resultText = generateResultText(mbti, loveType);
      const resultTextDiv = document.getElementById("resultText");
      resultTextDiv.innerHTML = resultText;
      resultTextDiv.style.display = "block";

      // フォームをリセット（何度でも回答可能）
      this.reset();
    });

    // 診断コメント生成関数
    function generateResultText(mbti, loveType) {
      let mbtiDesc = {
        INTJ: "戦略的で論理的なあなたは、恋愛でも自分の理想を大切にします。",
        INTP: "自由な発想と好奇心で恋愛を楽しむタイプです。",
        ENTJ: "リーダー気質で積極的な恋愛を好みます。",
        ENTP: "新しい刺激を求める恋愛探求者です。",
        INFJ: "深い共感力で相手を大切にするタイプです。",
        INFP: "理想主義で一途な恋愛を目指します。",
        ENFJ: "思いやりと行動力で恋愛をリードします。",
        ENFP: "明るく柔軟、好奇心旺盛な恋愛タイプです。",
        ISTJ: "誠実で信頼できる安定志向の恋愛タイプです。",
        ISFJ: "優しさと思いやりで相手を支えるタイプです。",
        ESTJ: "計画的に恋愛を進める現実主義者です。",
        ESFJ: "社交的で相手の気持ちに敏感なタイプです。",
        ISTP: "クールで自由な距離感を大切にします。",
        ISFP: "感受性豊かで自然体な恋愛を好みます。",
        ESTP: "行動的で新しい出会いを楽しむタイプです。",
        ESFP: "明るく盛り上げ役、楽しい恋愛を求めます。"
      };

      let loveDesc = {
        LCRO: "理論派で冷静なアプローチを好みます。",
        LCRE: "相手に誠実で論理的な関係を築きます。",
        LCPO: "主体性を持ちつつ冷静な恋愛をします。",
        LCPE: "積極的な行動力が恋愛に現れます。",
        LARO: "感情を大切にしつつ冷静な判断も忘れません。",
        LARE: "思いやりと理論のバランス型です。",
        LAPO: "自由な発想で恋愛を楽しみます。",
        LAPE: "積極的で感受性豊かな恋愛をします。",
        FCRO: "友情ベースで冷静な関係を築きます。",
        FCRE: "誠実で温かい心を持つ恋愛タイプです。",
        FCEO: "主体性と冷静さを兼ね備えています。",
        FCPE: "行動的で親しみやすい恋愛を好みます。",
        FARO: "感情豊かで冷静な判断もできるタイプです。",
        FAPE: "積極的なアプローチと感受性が特徴です。",
        FARE: "思いやりと積極性のバランス型です。",
        FAPO: "自由で感情表現が豊かな恋愛タイプです。"
      };

      return `<b>診断結果</b><br>
あなたのMBTIタイプ「<b>${mbti}</b>」は、${mbtiDesc[mbti] || ""}<br>
恋愛傾向「<b>${loveType}</b>」は、${loveDesc[loveType] || ""}<br>
この組み合わせは、あなたらしい恋愛のスタイルを示しています！`;
    }
  </script>
</body>
</html>
