# Project Topic Brief

# Mining Appliance Reviews for Failure and Service Complaints: Aspect-Based Classification and Ranking of Customer Issues

> **DSA 495 Topic Brief**
> 

## Team Members

- Marcelo Ballena

## One-Sentence Task

**Given a customer review of a home appliance, we will classify the complaint types it contains (e.g., reliability, noise, performance, delivery/installation, value) and aggregate them to rank the most common problems for each product or product category.**

## Illustrative Input and Desired Output

- **Example input:** (paraphrased, non-sensitive) “Bought this blender three months ago. It was powerful at first, but now it leaks from the bottom and the motor smells hot after a minute. Customer support took two weeks to answer.”
- **Desired output:** Complaint labels `reliability/failure` and `customer service`; evidence spans “leaks from the bottom”, “motor smells hot”, and “took two weeks to answer”; overall sentiment negative. Aggregated across all reviews of one product, the system returns a ranked list such as *1. leaking (31%), 2. motor overheating (22%), 3. slow support response (14%)*.

## Background and Starting Point

I am an Industrial Engineering student interested in operations and data-driven methods. This topic comes from a practical question in appliance retail: which product problems come up repeatedly, and how could a retailer learn about them early? My family runs an appliance retail business in Peru, which makes this a question I can connect to a real setting. Recurring complaints affect which products to stock, what to tell customers, and which supplier issues to raise. Online reviews are a large, free source of this information, but they are unstructured and too numerous to read by hand. This project is a first step toward turning them into something an operations team could act on.

## Intended Output and Success

The project should produce (a) a classifier or extractor that tags each review with complaint categories and evidence phrases, and (b) a summary view (tables and charts) ranking top complaint themes per product or category. Likely users are a retail operations or purchasing manager, or a consultant reviewing product quality for a retailer.

**Success statement:** The output is useful if a non-technical reader can look at the ranked complaint list for a product and, after spot-checking a sample of reviews, agree that it reflects the real problems customers describe.

## Preferred Data

### Corpus

One item in the corpus is one customer review of an appliance product. Relevant fields include the review text and title, star rating, product identifier (to roll reviews up by product), timestamp, and helpful-vote count; item metadata provides product titles and categories. The Appliances category contains millions of reviews. I plan to work with a sample of roughly 20,000-50,000 reviews, plus a hand-labeled subset of a few hundred for evaluation.

### Source and Access

- **Dataset or corpus name:** Amazon Reviews 2023, Appliances category
- **Original source organization or creator:** McAuley Lab, University of California San Diego
- **Original collection process:** Reviews and item metadata were collected from Amazon.com by the McAuley Lab and released for research use. The Hugging Face copy is a redistribution of that release.
- **Direct link:** [https://amazon-reviews-2023.github.io/](https://amazon-reviews-2023.github.io/) (also on Hugging Face: [https://huggingface.co/datasets/McAuley-Lab/Amazon-Reviews-2023](https://huggingface.co/datasets/McAuley-Lab/Amazon-Reviews-2023))
- **Access method:** Download from the project site or load with the Hugging Face `datasets` library.
- **Access, licensing, privacy, or redistribution considerations:** The data is released for research and academic use; I will confirm the exact terms on the project page. Reviews are public, but I will not redistribute the raw data in this repository. I will include only short excerpts and a script that downloads the data, and I will drop reviewer identifiers.
- **Backup corpus (optional):** Another Amazon Reviews 2023 category (e.g., Home and Kitchen) or another public product-review dataset. If time allows, a small set of Spanish-language product reviews to connect with the Peruvian retail context.

### Examples

Representative examples (illustrative descriptions; I will replace them with short real excerpts after my first data pull):

1. A 1-star review describing a part that stopped working after a short time.
2. A 3-star review that praises performance but complains about noise.
3. A 5-star review with no complaints, to test that the system does not over-tag.

### Fit with the Task

The reviews are real, free-text descriptions of product problems, star ratings give a rough sentiment signal, and product identifiers allow complaints to be aggregated per product. The main gap is that there are no complaint-category labels, so I will need to create a hand-labeled subset for training and evaluation.

## Feasibility and Immediate Next Steps

- **Minimum viable project:** Take a sample of appliance reviews, define 5-6 complaint categories, hand-label a few hundred reviews, build a baseline classifier (e.g., TF-IDF with logistic regression), and produce a ranked complaint table for several products.
- **Data-access check:** I have not yet downloaded or queried the data. The next access step is to download the Appliances sample and inspect its fields.
- **Largest current risk:** Defining complaint categories that are clear and consistent enough to label reliably. Vague categories would make the classifier and the rankings hard to trust.
- **Backup plan:** Reduce the project to fewer categories, or to a binary “product-failure complaint vs. no complaint” task, using star ratings and keyword rules as a weak baseline.
- **Next two actions:**
    1. Download the Appliances sample, inspect fields and text length, and save 3 real, non-sensitive example reviews. By October 28, 2026.
    2. Draft the complaint category scheme and hand-label about 100 reviews to test whether the categories are workable.  By November 4, 2026.

## Possible Text-Analysis Method and Evaluation

Possible methods: text cleaning and exploration (word frequencies, n-grams); a keyword/rule baseline; TF-IDF with logistic regression or a similar model for multi-label classification; topic modeling (e.g., LDA or BERTopic) to check whether my categories match themes in the data; possibly a pretrained transformer or an LLM for labeling or extracting evidence phrases.

Possible evaluation: precision, recall, and F1 per category on a hand-labeled test set; comparison against the keyword baseline; error analysis; and a manual check of the top-ranked complaints for several products against the underlying reviews. Methods and evaluation are still open and may change.

## Questions for the Instructor

- Is the scope (classification plus per-product ranking) appropriate, or should I narrow it to one of the two?
- Is a hand-labeled set of a few hundred reviews reasonable for evaluation, or would you expect more?

## AI-Use Statement

I used Claude to help me find datasets that could align to my project topic. Before consulting that, I had decided that I wanted a project connected to appliance retail and customer feedback. I will confirm the dataset links, size, and licensing terms directly on the dataset’s project pages.
