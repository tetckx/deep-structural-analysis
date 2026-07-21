---
name: deep-structural-analysis/exit
description: Exit and degradation protocols 鈥?Collapsed Mode, Ultra-Collapsed, Refusal handling, and architecture limitation. Load when user says "绠€鍗曠偣"/"璇翠汉璇?/"绠€鐭洖绛? or when degradation signals are detected.
version: 1.0.2
---

# Exit & Degradation Protocols

## Collapsed Mode

Trigger: user says "绠€鍗曠偣","璇翠汉璇?,"绠€鐭洖绛?,"give me the short version", or similar. Switch immediately.

Output (only these items):
1. **鏍稿績鍙戠幇** (2-3 鍙ヨ瘽)
2. **鈿狅笍 鍏抽敭鐩茬偣**锛堣嫢瀛樺湪鏌愪釜鐩茬偣浼氬疄璐ㄦ敼鍙樹釜浣撶瓥鐣モ€斺€旀渶澶氫竴鍙ヨ瘽銆傝嫢鏃犲垯鐪佺暐銆傦級
   - **鍒涗激鏁忔劅鎬х害鏉?*锛氬綋璇濋瑙﹀彂 Trauma-sensitive 鏍囧噯鏃讹紝鍏抽敭鐩茬偣涓ョ瀵圭О鍙ュ紡銆傛湁鏁堢ず渚嬶細"瀹夊叏鎴愭湰鍜屾毚鍔涢闄╀笉鍦ㄥ悓涓€涓噺绾?銆傝繚瑙勭ず渚嬶細"鍙屾柟閮介渶瑕佸喎闈?銆?3. **鍒嗗眰褰卞搷琛?* (绯荤粺 / 鍒跺害 / 涓綋 脳 鐭湡 / 涓湡 / 闀挎湡)
4. **涓€涓拷闂?*: "闇€瑕佹垜灞曞紑鏌愪竴閫忛暅鎴栧伐鍏风殑璇︾粏鍒嗘瀽鍚楋紵"鈥斺€斿垱浼ゆ晱鎰熻瘽棰樹笂锛岃拷闂笉寰楄姹傚彈瀹宠€?鐞嗚В瀵规柟"銆?
## Ultra-Collapsed锛堜簩娆￠檷绾э級

Trigger: user responds to Collapsed with "鍐嶇畝鍗曠偣","璇翠汉璇?,"涓€鍙ヨ瘽". Drop the table.

1. **涓€鍙ヨ瘽鏍稿績鍙戠幇**
2. **涓€鏉″彲琛屽姩涓綋寤鸿**锛堚墹20 涓腑鏂囧瓧绗︼級
3. **涓€鏉￠闄╂彁绀?*锛堝閫傜敤鍒欎繚鐣欙紝鍚﹀垯鐪佺暐锛?
绾枃鏈紝鏃犺〃鏍硷紝鏃犺拷闂€?
## Refusal Handling

If user declines to choose after TWO clarification attempts ("浣犺嚜宸卞垽鏂?/"鑷鍒ゆ柇"/"鎴戜笉鍙備笌"/"I won't participate"):

1. Default to LOWER-effort option. Decision heuristic:
   - **鐭洖绛?*锛堢函鏂囨湰锛屸墹100 涓枃瀛楃锛屾棤琛ㄦ牸锛屾棤鏉垮潡鏍囬锛夛細涓汉/涓村簥缁村害锛?鎴戜负浠€涔?.." / "鎴戞€庝箞鎵嶈兘..." / "鎴戣涓嶈..."锛夛紝鐢ㄦ埛瀵绘眰寤鸿鑰岄潪鍒嗘瀽銆傜ず渚嬶細"鎴戜负浠€涔堟€绘槸澶辩湢" 鈫?鐭洖绛?鍙寤鸿锛屼笉鍋氱潯鐪犵瀛︾殑鑱氱劍鍒嗘瀽銆?*鐭洖绛旀牸寮?*锛氫竴涓嚜鐒舵钀斤紝鐩存帴鍥炵瓟鏍稿績鍏冲垏銆備笉闇€瑕佹澘鍧楁爣棰橈紙"鏍稿績鍙戠幇"绛夛級鈥斺€旂敤鎴疯鐨勬槸绛旀鏈韩锛屼笉鏄垎鏋愮粨鏋勩€?   - **鑱氱劍娣卞害**锛?-4閫忛暅锛屾墽琛屾憳瑕佸惈琛ㄦ牸锛夛細鍗充娇涓汉妗嗗畾锛屼絾瑙﹀強缁撴瀯鍩燂紙缁忔祹銆佹斂绛栥€佺ぞ浼氳鑼冿級銆傜ず渚嬶細"鎴戜负浠€涔堝瓨涓嶄笅閽? 鈫?鑱氱劍锛屽洜涓轰釜浜鸿储鍔＄粨鏋勬€у祵鍏ュ伐璧勫闀裤€侀€氳儉鍜屾秷璐规枃鍖栥€?   - **妯＄硦鏃堕粯璁よ仛鐒︽繁搴?*銆傜敤鎴峰彲缁х画鎶樺彔锛?璇翠汉璇?锛夛紝浣嗗睍寮€闇€瑕佹柊涓€杞氦浜掋€?2. 鏄惧紡澹版槑榛樿鍊硷細"鎴戝皢閲囩敤[绠€鐭洖绛?鑱氱劍娣卞害鍒嗘瀽]锛屽闇€鏇存繁鍏ヨ闅忔椂鍛婄煡銆?
3. **鍘熺悊**锛氫袱娆℃嫆缁濋€夋嫨鐨勭敤鎴峰湪琛ㄨ揪涓嶈€愮儲锛屼笉鏄姹傛繁搴︺€傚畞鍙粰灏戜簡璁╃敤鎴疯"灞曞紑"锛屼篃鍒粰澶氫簡璁╃敤鎴疯寰?浣犱笉鍚垜璇磋瘽"銆?4. 灞曞紑閫氶亾淇濈暀锛氱敤鎴峰悗缁"灞曞紑"鎴?璇︾粏鍒嗘瀽"鏃讹紝鐩存帴鍗囩骇娣卞害锛屼笉閲嶆柊闂師濮嬫緞娓呴棶棰樸€?
> **浼樺厛绾ц鏄?*锛歊efusal 浜х敓鐨?鐭洖绛?鎴?鑱氱劍娣卞害"鏄垎鏋愮殑璧峰绾у埆鈥斺€旀瘮 Collapsed 鏇存棭瑙﹀彂锛堝彂鐢熷湪瀹屾暣鍒嗘瀽鍚姩涔嬪墠锛夈€傚鏋滅敤鎴峰湪 Refusal 浜х敓鐨勮仛鐒︽繁搴﹁緭鍑哄悗璇?璇翠汉璇?锛岀户缁蛋 Collapsed鈫扷ltra-Collapsed 閾炬潯銆?
## Architecture Limitation

Mid-generation interruption (user sends "璇翠汉璇? during analysis) cannot be guaranteed by Skill text alone. Best-effort: (1) check for new input at Phase/lens/tool boundaries 鈥?between output sections, when switching lenses, after completing a tool application, (2) discard un-emitted plans, (3) if partial analysis already output, prepend "[宸插垏鎹㈣嚦鎶樺彔妯″紡]".
