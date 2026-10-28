### ==🔴1. **what is a RAG:**==
Retrieval augmented generation (RAG) is a technique that combines information retrieval with language model.
combine with two system:
- Information Retrieval System: search for information in Knowledge Base.
- Generative Language Model: add this info to the model prompt to generate answer based on this added info.
![245](data:image/svg+xml;charset=utf-8,%3Csvg%20font-family%3D%22-apple-system-body%2C%20ui-sans-serif%2C%20-apple-system%2C%20system-ui%2C%20%26quot%3BSegoe%20UI%26quot%3B%2C%20Helvetica%2C%20%26quot%3BApple%20Color%20Emoji%26quot%3B%2C%20Arial%2C%20sans-serif%2C%20%26quot%3BSegoe%20UI%20Emoji%26quot%3B%2C%20%26quot%3BSegoe%20UI%20Symbol%26quot%3B%22%20font-weight%3D%22400%22%20data-d-component%3D%22svg%22%20fill%3D%22currentColor%22%20style%3D%22color%3Argb\(13%2C%2013%2C%2013\)%22%20viewBox%3D%220%200%20340%20400%22%20width%3D%22100%25%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Crect%20x%3D%228%22%20y%3D%229%22%20width%3D%22153%22%20height%3D%22105%22%20rx%3D%2210%22%20fill%3D%22%232185D0%22%20fill-opacity%3D%22.09%22%20stroke%3D%22%232185D0%22%20stroke-opacity%3D%22.45%22%2F%3E%3Ctext%20x%3D%2284%22%20y%3D%2229%22%20fill%3D%22currentColor%22%20font-size%3D%2212%22%20font-weight%3D%22600%22%20text-anchor%3D%22middle%22%3EINDEXING%3C%2Ftext%3E%3Crect%20x%3D%2222%22%20y%3D%2240%22%20width%3D%22125%22%20height%3D%2224%22%20rx%3D%225%22%20fill%3D%22%232185D0%22%20fill-opacity%3D%22.16%22%2F%3E%3Ctext%20x%3D%2284%22%20y%3D%2256%22%20fill%3D%22currentColor%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%3EvLLM%20Repository%3C%2Ftext%3E%3Cpath%20d%3D%22M84%2065%20V78%22%20stroke%3D%22%232185D0%22%20stroke-width%3D%221.5%22%2F%3E%3Cpath%20d%3D%22M80%2074%20L84%2079%20L88%2074%22%20fill%3D%22none%22%20stroke%3D%22%232185D0%22%20stroke-width%3D%221.5%22%2F%3E%3Crect%20x%3D%2222%22%20y%3D%2280%22%20width%3D%22125%22%20height%3D%2224%22%20rx%3D%225%22%20fill%3D%22%232185D0%22%20fill-opacity%3D%22.16%22%2F%3E%3Ctext%20x%3D%2284%22%20y%3D%2296%22%20fill%3D%22currentColor%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%3EChunking%3C%2Ftext%3E%3Crect%20x%3D%22179%22%20y%3D%229%22%20width%3D%22153%22%20height%3D%22105%22%20rx%3D%2210%22%20fill%3D%22%23159D7B%22%20fill-opacity%3D%22.09%22%20stroke%3D%22%23159D7B%22%20stroke-opacity%3D%22.45%22%2F%3E%3Ctext%20x%3D%22255%22%20y%3D%2229%22%20fill%3D%22currentColor%22%20font-size%3D%2212%22%20font-weight%3D%22600%22%20text-anchor%3D%22middle%22%3ERETRIEVAL%3C%2Ftext%3E%3Crect%20x%3D%22193%22%20y%3D%2240%22%20width%3D%22125%22%20height%3D%2224%22%20rx%3D%225%22%20fill%3D%22%23159D7B%22%20fill-opacity%3D%22.16%22%2F%3E%3Ctext%20x%3D%22255%22%20y%3D%2256%22%20fill%3D%22currentColor%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%3EUser%20Question%3C%2Ftext%3E%3Cpath%20d%3D%22M255%2065%20V78%22%20stroke%3D%22%23159D7B%22%20stroke-width%3D%221.5%22%2F%3E%3Cpath%20d%3D%22M251%2074%20L255%2079%20L259%2074%22%20fill%3D%22none%22%20stroke%3D%22%23159D7B%22%20stroke-width%3D%221.5%22%2F%3E%3Crect%20x%3D%22193%22%20y%3D%2280%22%20width%3D%22125%22%20height%3D%2224%22%20rx%3D%225%22%20fill%3D%22%23159D7B%22%20fill-opacity%3D%22.16%22%2F%3E%3Ctext%20x%3D%22255%22%20y%3D%2296%22%20fill%3D%22currentColor%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%3EQuery%20Processing%3C%2Ftext%3E%3Cpath%20d%3D%22M84%20115%20V136%20H170%20V149%22%20fill%3D%22none%22%20stroke%3D%22currentColor%22%20stroke-opacity%3D%22.5%22%20stroke-width%3D%221.5%22%2F%3E%3Cpath%20d%3D%22M255%20115%20V136%20H170%22%20fill%3D%22none%22%20stroke%3D%22currentColor%22%20stroke-opacity%3D%22.5%22%20stroke-width%3D%221.5%22%2F%3E%3Crect%20x%3D%2287%22%20y%3D%22150%22%20width%3D%22166%22%20height%3D%2238%22%20rx%3D%228%22%20fill%3D%22%23159D7B%22%20fill-opacity%3D%22.15%22%20stroke%3D%22%23159D7B%22%20stroke-opacity%3D%22.5%22%2F%3E%3Ctext%20x%3D%22170%22%20y%3D%22166%22%20fill%3D%22currentColor%22%20font-size%3D%2212%22%20font-weight%3D%22600%22%20text-anchor%3D%22middle%22%3EBM25%20%2F%20TF-IDF%3C%2Ftext%3E%3Ctext%20x%3D%22170%22%20y%3D%22179%22%20fill%3D%22currentColor%22%20font-size%3D%2210%22%20text-anchor%3D%22middle%22%3EIndex%20%26amp%3B%20Ranking%3C%2Ftext%3E%3Cpath%20d%3D%22M170%20189%20V210%22%20stroke%3D%22currentColor%22%20stroke-opacity%3D%22.6%22%20stroke-width%3D%221.5%22%2F%3E%3Cpath%20d%3D%22M166%20205%20L170%20211%20L174%20205%22%20stroke%3D%22currentColor%22%20fill%3D%22none%22%20stroke-width%3D%221.5%22%2F%3E%3Crect%20x%3D%2287%22%20y%3D%22212%22%20width%3D%22166%22%20height%3D%2236%22%20rx%3D%228%22%20fill%3D%22%23159D7B%22%20fill-opacity%3D%22.15%22%20stroke%3D%22%23159D7B%22%20stroke-opacity%3D%22.5%22%2F%3E%3Ctext%20x%3D%22170%22%20y%3D%22234%22%20fill%3D%22currentColor%22%20font-size%3D%2212%22%20font-weight%3D%22600%22%20text-anchor%3D%22middle%22%3ETop-K%20Snippets%3C%2Ftext%3E%3Cpath%20d%3D%22M170%20249%20V270%22%20stroke%3D%22currentColor%22%20stroke-opacity%3D%22.6%22%20stroke-width%3D%221.5%22%2F%3E%3Cpath%20d%3D%22M166%20265%20L170%20271%20L174%20265%22%20stroke%3D%22currentColor%22%20fill%3D%22none%22%20stroke-width%3D%221.5%22%2F%3E%3Crect%20x%3D%2260%22%20y%3D%22272%22%20width%3D%22220%22%20height%3D%2244%22%20rx%3D%228%22%20fill%3D%22%23B784E7%22%20fill-opacity%3D%22.13%22%20stroke%3D%22%23A76CD1%22%20stroke-opacity%3D%22.65%22%2F%3E%3Ctext%20x%3D%22170%22%20y%3D%22289%22%20fill%3D%22currentColor%22%20font-size%3D%2212%22%20font-weight%3D%22600%22%20text-anchor%3D%22middle%22%3EQwen3-0.6B%3C%2Ftext%3E%3Ctext%20x%3D%22170%22%20y%3D%22304%22%20fill%3D%22currentColor%22%20font-size%3D%2210%22%20text-anchor%3D%22middle%22%3EQuestion%20%2B%20Retrieved%20Context%3C%2Ftext%3E%3Cpath%20d%3D%22M170%20317%20V338%22%20stroke%3D%22currentColor%22%20stroke-opacity%3D%22.6%22%20stroke-width%3D%221.5%22%2F%3E%3Cpath%20d%3D%22M166%20333%20L170%20339%20L174%20333%22%20stroke%3D%22currentColor%22%20fill%3D%22none%22%20stroke-width%3D%221.5%22%2F%3E%3Crect%20x%3D%2287%22%20y%3D%22340%22%20width%3D%22166%22%20height%3D%2240%22%20rx%3D%228%22%20fill%3D%22%23B784E7%22%20fill-opacity%3D%22.13%22%20stroke%3D%22%23A76CD1%22%20stroke-opacity%3D%22.65%22%2F%3E%3Ctext%20x%3D%22170%22%20y%3D%22357%22%20fill%3D%22currentColor%22%20font-size%3D%2212%22%20font-weight%3D%22600%22%20text-anchor%3D%22middle%22%3EFinal%20Answer%3C%2Ftext%3E%3Ctext%20x%3D%22170%22%20y%3D%22370%22%20fill%3D%22currentColor%22%20font-size%3D%2210%22%20text-anchor%3D%22middle%22%3EStructured%20JSON%20Output%3C%2Ftext%3E%3C%2Fsvg%3E)

> after reading our source that we have , we should chunk them to be easy for us to searching and indexing , and with using data structure named ==🟢inverted index==

**inverted index :**
An inverted index is an index data structure storing a mapping from content, such as words or numbers, to its locations in a document or a set of documents. In simple words, it is a [hashmap-like data structure](https://www.geeksforgeeks.org/dsa/hashing-data-structure/) that directs you from a word to a document or a web page. They are especially useful for large collections of documents, where searching through all the documents would be prohibitively slow.
![[Pasted image 20261024124716.png]]      ![[Pasted image 20261024124735.png]]

and with that in order of reading all chunking source with every single query , we use ==🟢inverted index== so each term we index it in which document belongs to.
now we have a query and indexed chunks, so next is to :
1. Tokenize this query with same strategy that we do to our documents.
2. get matching chunks with the tokens of query and now we have candidate chunks.
3. ==🟡BM25 Scoring==: calculate relevente score for every candidate chunk with :
   ![[Pasted image 20261024114745.png]]
4. Get top-k from the candidate chunks

**RESUME THIS :**
> ==🟣The system preprocesses and tokenizes the query using the same tokenizer as the indexing stage. It then computes BM25 relevance scores over indexed chunks, ranks them, and selects the Top-K results. Each selected chunk is mapped back to its original file path and character offsets. For answer generation, the retrieved chunk contents are added to the prompt and passed to Qwen3-0.6B to generate a grounded answer.==

### ==🔴2. BM25 (Best Match 25): probabilistic ranking function==

In simple Information retrieval algorithm, BM25 helps rank documents or web pages based on how well they match a user’s search terms making it a cornerstone of effective search and retrieval systems.

In general it working to compute a relevance score between a query and a doc using three main compoents: **==🟣Term Frequency (TF), Inverse Document Frequency (IDF) and Document Length Normalization.==**
![[Pasted image 20261025095901.png|391]]

Overall, BM25 is based around three questions, with no requirement for neural networks (refer to the image below again):

![[Pasted image 20261027183745.png|598]]

**BM25 asks three simple questions:**

1. ==🔴**"How rare is this word ? "**==
every chunk contain "the" and "is", which makes them useless, but when the word became "transformer" (for exp) is a specific and informative, so the word will be boosted.
==🟢this is IDF(qi) in the formula== 
IDF --- Inverse Document Frequency and calculate the rarity of this word we use this formula: 
![[Pasted image 20261025100725.png]]
2. ==🔴**“How many times does it appear?”**==
let's say we found "Transformer" repeat 10 times in a chunk , we can say that this chunk talk about it , but if other chunk contain the word 100 times that's not mean that this not score x10 better that the first one.
![[Pasted image 20261025101316.png|418]]
in the first we saw that The curve how it up in first and how it continue after 10 repeats because the diff between 1 repeat and 10 is must important.
==🟢This is `f(qᵢ, D)` combined with `k₁` that controls saturation==
Term Frequency Saturation:
![[Pasted image 20261025102128.png]]
==🟡The question here is why we use k as paramter and we dont use log or ln:==
in this formula of term saturation :
![[Pasted image 20261028104931.png|277]]
let take L = 1 so the formula will bccome : 
![[Pasted image 20261028105050.png]]
and for k = 1.5
so here if we calculate the limite of this function :
![[Pasted image 20261028105519.png|240]] 
k + 1 = 2.5
well the contribution will never up to 2.5 even if the term repeated 1000 of times.
but if we use here logarithm like idf.


3. **==🔴“Is this document unusually long?”==**
A 50-page paper will naturally contain more keywords than a 5-page paper. BM25 levels the playing field so longer documents don’t cheat their way to the top.

==🟢This is **|D|/avgdl** controlled by parameter b==
![[Pasted image 20261025102358.png]]
==🟢let's calculate it by an exemple:==
- Doc A with 100 Tokens
- Doc B with 500 Tokens
- average Doc len 200 Tokens
- b = 0.75
For A :
![[Pasted image 20261025102619.png]]
For B: 
![[Pasted image 20261025102640.png]]
whenever L grow contribution of Term go down, so that BM25 try to minimalize the advatage the can get a big doc.

### ==🔴3. Tf-IDF(Term Frequency - Inverse Document Frequency):==

In one SHOOOOOT:
#### ==🟢TF - Term Frequency:==
Measures how often a word appears within a single document[1]. It is calculated by counting how many times the word appears in the document and dividing that count by the total number of words in that document
![[Pasted image 20261025113228.png|426]]
==🔴`In mathematical ans algo`:==
$$TF(t, d) = f_{t,d}$$
==🔵**wlkin lmochkil li ghad iykon hna how ila chi klma t3awdat 100 mra donc ghatkon 7ssen b x100 mn klma t3awdat ghir mra.**==
==🔵bach n7alo lmochkil kansta3mlo **Sublinear TF Scaling**==

$$TF_{sublinear}(t, d) = \begin{cases} 1 + \log(f_{t,d}) & \text{if } f_{t,d} > 0 \\ 0 & \text{otherwise} \end{cases}$$
had lformula katkhali l importance ytl3 bchwiya , matalan term t3awd 10 dlmrat :
1 + log(10) = 2
so ghaywali lwazn dyalo 2 machi 10 , ohadchi ghaykhali ykon far mabin kalma t3awdat mra o 10 wlkin maghaykon far9 bzf mabin 10 o 30.


#### ==🟢IDF - Inverse Document Frequency==
Measures how rare or common a word is across the **entire collection of documents**[2]. Highly common words (such as "the", "is", or "of") appear frequently everywhere but carry very little unique meaning[1][2]. IDF reduces the weight of these common words by assigning them **lower scores**, while assigning **higher scores** to rarer words
![[Pasted image 20261025113414.png|428]]

==🔴`In mathematical ans algo`:=='

$$IDF(t, D) = \log\left(\frac{N}{df_t}\right)$$
هنا $N$ هو العدد الإجمالي ديال المستندات، و $df_t$ هو عدد المستندات اللي كتحتوي على الكلمة $t$. اللوغاريتم تدار باش ما يعطيش أوزان خيالية للكلمات النادرة جداً، وباش يضغط المجال ديال الأرقام.

**علاش هاد المعادلة فيها خلل رياضي وكيفاش تصلحات؟** كاين مشكل رياضي فهاد المعادلة: إيلا كانت الكلمة كاينة فكاع المستندات ($df_t = N$)، فإن الكسر كيولي $N/N = 1$. اللوغاريتم ديال 1 هو 0 ($IDF = \log(1) = 0$). هادشي كيعني أن الكلمة غيتم الإلغاء ديالها تماماً (وزنها غيولي 0) وخا تكون عندها شي أهمية ثانوية. المشكل 
الثاني هو إيلا كانت الكلمة ماكايناش كاع، غيوقع لينا خطأ ديال القسمة على صفر (Division by Zero).
bach n7alo had lmochkil f library Scikiy_learn il zadna (smooth_idf = True) ghadi tsta3mal function named: ==🟡Smoothed idf==

$$IDF_{smooth}(t, D) = \log\left(\frac{N + 1}{df_t + 1}\right) + 1$$

- **علاش تزادت +1 فالكسر؟** كيتعامل مع النظام رياضياً بحال إيلا كاين مستند وهمي إضافي كيحتوي على كاع الكلمات ديال القاموس بالضبط مرة وحدة. هادشي كيمنع القسمة على صفر إيلا الكلمة ماكانتش.
    
- **علاش تزادت +1 برا اللوغاريتم؟** باش نضمنو أن الـ IDF عمرو ما يهبط لـ 0. حتى الكلمات الشائعة جداً اللي كاينة فكل المستندات غيبقا عندها وزن أدنى ديال 1. هادشي كيحافظ على وزن الـ TF ديالها بلا ما يتضرب فـ 0 ويتمسح.
#### ==🟢Final Result==
multiplying the **Term Frequency** by the **Inverse Document Frequency** (TF × IDF), the method produces a final score where a **higher TF-IDF score** signals **greater importance** for that word within the specific document
![[Pasted image 20261025113436.png|477]]

#### ==🟢Vector Space Model:==

before we compare Query with Documents , we present each doc to a vector of TF-idf weight.
len of vector is determined by the total vocabulary of your document collection, but it is simplified when presenting or visualizing the results:
**Vocabulary Size**: The length (or size) of a TF-IDF vector is equal to the **total number of unique words across the entire collection of documents**
==🟣Each position in this vector present the same Term in all document.==

### Cosine Similarity :

##### ==🔴What is cosine?==

Two vectors, `q` and `d`, in a space with one dimension per vocabulary term. They have an **angle θ** between them. Cosine of that angle measures how much they **point in the same direction**.

we get this formula from calculated the dot.product of two vector:
**a · b** = |**a**| × |**b**| × cos(θ)
and then:
cos(θ) = **a · b**  / |**a**| × |**b**|
Where:  
|**a**| is the magnitude (length) of vector **a**  
|**b**| is the magnitude (length) of vector **b**  
**θ is the angle between** **a** and **b**

So we multiply the length of **a** times the length of **b**, then multiply by the cosine of the angle between **a** and **b**

**a · b** = ax × bx + ay × by
|a| = 
![[Pasted image 20261025115449.png]]
Use of this expression to calculate the semantic between query and doc, and then focus on the trend of the vector.
Similarity close to 1 : vectors more sementic
Similarity close to 0 : there is no overlao between Terms
but -1 : indicates that the vectors point in exactly opposite directions.
### تسوية المتجهات (Vector Normalization) - L1 مقابل L2

المستندات الطويلة كتحتوي على كلمات كتر، وهادشي كيعني أن المتجهات ديالها غتكون الأطوال ديالها كبيرة بزاف، وغيكون فيها تكرار أكثر. باش نقارنو مستند طويل مع مستند قصير بعدل، كيخصنا نديرو التسوية (Normalization) باش نحيدو تأثير الطول.

**L2 Normalization (التسوية الإقليدية):** هاد الطريقة كتقسم كل قيمة فالمتجه على الطول الإقليدي الإجمالي للمتجه (Euclidean Norm). المعادلة هي:

$$\hat{v}_i = \frac{v_i}{||v||_2} = \frac{v_i}{\sqrt{\sum_{j=1}^{n} v_j^2}}$$

- **شنو كيعني هادشي هندسياً؟** كيهبط المتجه أو كيطولو باش يولي الطول ديالو (Magnitude) كيساوي بالضبط 1. هادشي كيخلي كاع المتجهات ديال كل المستندات يطيحو فوق قشرة ديال كرة هندسية (Unit Hypersphere) فالفضاء المتعدد الأبعاد.
    
- **علاش كيتستعمل L2 كخيار افتراضي؟** حيت عندو علاقة رياضية سحرية ومباشرة مع Cosine Similarity. إيلا كانو المتجهات بجوج خضعو لـ L2 Normalization، فإن حساب الـ Cosine Similarity كيولي هو فقط الضرب النقطي (Dot Product) بلا ما نحتاجو نقسمو على الأطوال.
    

**L1 Normalization (تسوية مانهاتن):** هاد الطريقة كتقسم كل قيمة على المجموع المطلق ديال كل القيم اللي فالمتجه:

$$\hat{v}_i = \frac{v_i}{||v||_1} = \frac{v_i}{\sum_{j=1}^{n} |v_j|}$$

- **فين كيتستعمل L1؟** كيتستعمل فاش كنبغيو أن المجموع ديال القيم فالمتجه يكون كيساوي 1. هادشي كيعطينا توزيع احتمالي (Probability Distribution) لكل كلمة فالمستند. كيتستعمل كذلك فخوارزميات التصنيف (Classification) حيت كيشجع على الـ Sparsity وكيصغر القيم الضعيفة لدرجة كيخليها أصفار.
    

### تشابه جيب التمام (Cosine Similarity)

باش نحسبو شحال جوج دالمستندات كيتشابهو، ولا شحال المستند كيطابق سؤال المستخدم (Query)، كنستعملو Cosine Similarity. المعادلة الأصلية كتحسب جيب التمام ديال الزاوية $\theta$ بين جوج ديال المتجهات $A$ و $B$:

$$\cos(\theta) = \frac{A \cdot B}{||A||_2 ||B||_2} = \frac{\sum_{i=1}^{n} A_i B_i}{\sqrt{\sum_{i=1}^{n} A_i^2} \sqrt{\sum_{i=1}^{n} B_i^2}}$$

**علاش تم اختيار الزاوية وليس المسافة (Euclidean Distance)؟** إيلا استعملنا المسافة الإقليدية، المستند الطويل غيكون بعيد بزاف فالفضاء على المستند القصير، حتى إيلا كانو كيهضرو على نفس الموضوع بالظبط (حيت المتجه ديال المستند الطويل غادي يكون بعيد عن نقطة الصفر). ولكن الزاوية $\theta$ كتقيس "الاتجاه" ديال المتجه وليس "الطول" ديالو. إيلا كانت الزاوية 0 (يعني كيمشيو فنفس الاتجاه)، فـ $\cos(0) = 1$ (تطابق تام).

_ملاحظة هامة:_ كما شُرِح سابقاً، إيلا تم تطبيق L2 Normalization على المتجهات مسبقاً فمرحلة سابقة، فإن الأطوال $||A||_2$ و $||B||_2$ كتولي كتساوي 1. الكسر اللي فالمقام كيولي $1 \times 1 = 1$. وبالتالي المعادلة كتبسط وكتولي فقط:

$$\cos(\theta) = A \cdot B = \sum_{i=1}^{n} A_i B_i$$

هاد التبسيط الرياضي كيسرع عملية البحث بملايين المرات فالأنظمة الحقيقية، حيت الضرب والجمع أسرع بكتير من حساب الجذور المربعة فكل عملية استعلام.

