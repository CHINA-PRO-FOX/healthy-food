# Healthy Food: A Multi-Agent Based Food Image Recognition and Precision Weight Management Platform

> A full-scenario weight loss and health management agent system centered on evidence-traceable food recognition and calorie calculation, integrating multi-model collaboration and long-term memory mechanisms.

Healthy Food is a full-chain weight management platform driven by a Multi-Agent architecture, integrating the capabilities of DeepSeek, Doubao, Kimi, and other models into a unified collaborative system. Through food image recognition, ingredient analysis, health assessment, dynamic intervention, and long-term management, the platform addresses core issues of traditional weight loss software, such as distorted data collection, templated solutions, and inadequate coverage of special populations.

## Why It's Not an Ordinary Calorie Tracking Tool

- **Multi-Model Collaborative Recognition**: Single models struggle with the fragmented visual features of complex Chinese cuisine. Healthy Food employs multi-agent division of labor to concurrently perform food category recognition, weight estimation, nutritional calculation, and health recommendation generation.
- **3D Reconstruction via Reference Objects**: Instead of relying on subjective user estimation of weight, the system calculates container volume using reference objects such as tableware and hands, combined with ingredient proportions to compute dish weight, achieving over 60% improvement in accuracy over traditional "bowl/spoon" measurements.
- **Dynamic Interactive Error Correction**: Users can supplement contextual information such as "less oil" or "add fried bean curd," triggering the multi-agent system to re-analyze and correct calorie and nutrition data in real time, forming a "recognition–assessment–correction" feedback loop.
- **Independent Modules for Special Populations**: Dedicated algorithms are developed for six special groups—allergy sufferers, diabetics, adolescents, the elderly, postpartum women, and individuals with extreme obesity—to avoid health risks associated with one-size-fits-all approaches.
- **Emotional Companionship and Long-Term Management**: An integrated affective computing module detects emotional signals and provides psychological interventions; time-series forecasting predicts plateaus and relapse risks, driving the transition from short-term weight loss to lifelong health management.

## Currently Verifiable Capabilities

The following metrics are derived from internal testing and real-world scenario validation:

| Capability | Metric |
|------------|--------|
| Chinese Cuisine Recognition | 79 categories, 92.3% accuracy on test set |
| Ingredient Breakdown | Up to 12 ingredients recognized per image (confidence > 85%) |
| Nutritional Database Coverage | 327 ingredients, 4-dimensional data (calories/protein/fat/carbs) |
| Smart Suggestion Latency | < 1.8 seconds (Qwen version) |
| Weight Estimation Accuracy Improvement | > 60% over traditional methods |
| Calorie Calculation Error Reduction | 40% lower than traditional database matching |
| Long-Text Generation Speed | 6,800-word market analysis in 116 seconds, structural completeness 91.4% |

These results are derived from comparative experiments and user testing during development and do not represent large-scale clinical validation. Full experimental details and limitations are provided in the "Validation and Boundaries" section.

## Core Workflow

```
User takes food photo / provides text description
        │
        ▼
Multi-modal Feature Extraction (Doubao + Kimi Vision, DeepSeek Semantics)
        │
        ▼
Multi-Agent Collaborative Reasoning (Recognition + Weight Estimation + Nutrition Calculation)
        │
        ▼
Interactive Validation (Display candidate answers, user confirms or corrects)
        │
        ▼
Dynamic Health Plan Generation (Integrates user profile, long-term memory, environmental data)
        │
        ▼
Continuous Tracking & Adaptive Adjustment (Emotional companionship + Plateau prediction)
```

## Technical Architecture

### Agent and Model Matrix

The platform builds a Multi-Agent collaboration network based on the Coze platform, with core models including:

| Role | Model | Responsibility |
|------|-------|----------------|
| Core Orchestration | Coze Base Model | Task routing and process control |
| Complex Reasoning | DeepSeek-R1 / V3 0324 / Distill-Qwen-7B/32B | Multi-step logical deduction, calorie formula derivation, nutrition report generation |
| Multi-modal Vision | Doubao Vision Understanding-1.5-pro / Lite | Food image recognition, weight reference analysis, OCR for packaging information extraction |
| Interaction & Generation | Kimi Large Model, Doubao General-pro | Natural language feedback, personalized recommendations, emotional companionship dialogue |
| Auxiliary Agents | Tongyi Qianwen-Max, Zhipu·4, Minimax abab6.5s, Stepfun 1v-Image Understanding, Baichuan-4 | Supplementary reasoning, image understanding, long-context processing |

All models are invoked via a unified API gateway using the JSON-RPC protocol, with response times controlled within 800ms.

### Plugin Ecosystem

| Plugin Type | Representative Plugins | Function |
|-------------|------------------------|----------|
| Information Retrieval | biyingsousuo-bingWebSearchLight / WebSearch | Real-time access to nutritional data, weather, news |
| Link Parsing | lianjieduqu-LinkReaderPlugin | Extract content from PDF, DOCX, web pages |
| Image Understanding | tupianlijie-imgUnderstand | Dish recognition + nutritional database comparison, output calories/allergens/health advice |
| Specialized Processing | img_cat-image_divider | Identify object positions in images, assist reference object localization |
| AI Generation | ByteArtist – ImageToolPro, byteartist-text2image | Text-to-image, image-to-image, multi-style output |
| Code Execution | daimazhixingqi-CodeRunner | Temporary sandbox Python execution, mathematical computation |
| Weather Services | mojitianqi-DayWeather, OpenWeather, WeatherQueryPlugin | Weather and environmental data for dynamic plan adjustment |
| Mind Mapping | TreeMindshutu-generateTreeMind | Convert text to structured mind maps |

### Long-Term Memory Technology

Adopts a dual-track approach combining structured databases and knowledge graphs:

- **Structured Storage**: User dietary records and health metrics (blood glucose, blood pressure, etc.) are stored in standardized format for efficient querying.
- **Knowledge Graph Association**: Visualizes associations between food nutrition, calorie data, and user preferences to uncover potential health risks and improvement opportunities.
- **Dynamic Updates**: Based on user feedback and new data, agents automatically iterate algorithmic parameters, updating recognition models and calorie calculation parameters.

### Workflow Pipeline

The system implements a four-stage tool flow for full automation from image input to health recommendations:

1. **Feature Extraction**: Concurrently invokes Doubao and Kimi for visual feature extraction (ResNet50-based), combined with DeepSeek semantic analysis, generating multi-modal feature vectors.
2. **Collaborative Reasoning**: Dynamically assigns the primary reasoning agent (DeepSeek leading for complex dishes), integrating knowledge graph evidence to output candidate recognition results.
3. **Interactive Validation**: Presents candidate answers to users via the interaction agent (e.g., "Could be: ① Braised Pork ② Meicai Kou Rou"), triggering correction based on user feedback.
4. **Action Output**: Based on final results, integrates with external interfaces for health management, meal recommendations, exercise planning, forming a service closed loop.

## Core Functional Modules

### 1. Precision Food Image Recognition

- **Fine-Grained Ingredient Analysis**: Pixel-level analysis of food categories, ingredient composition, and proportions; supports simultaneous recognition of multiple dishes on a table.
- **3D Reconstruction for Weight Estimation**: Uses reference objects such as tableware and hands to calculate container volume, combined with ingredient density to compute weight; supports fractional measurements (e.g., 1/3 bowl).
- **Knowledge Graph Calorie Precision**: Integrates ingredient properties, cooking techniques, nutritional components, and other associated data to dynamically calculate calories and nutrition, reducing error rates by 40% compared to traditional methods.

### 2. Deeply Personalized Dynamic Health Plans

- **User Profile Construction**: Cross-modal fusion of dietary images, medical reports, and exercise data to build a comprehensive health profile.
- **Multi-Dimensional Analysis**: Considers 20+ factors including BMI, metabolic rate, allergens, special conditions, taste preferences, sleep quality, emotional state, and weather conditions.
- **Dynamic Adjustment**: Time-series analysis predicts plateaus and relapse risks, automatically adjusting diet and exercise plans. For example, if exercise goals are missed for 3 consecutive days, AI reduces intensity and recommends a "light fasting" diet; on smoggy days, automatically switches to indoor exercises.
- **Feedback Loop**: Collects user evaluations of plans, continuously adjusting algorithmic parameters.

### 3. Independent Algorithm Modules for Six Special Populations

| Population | Core Challenge | Healthy Food Solution |
|------------|----------------|----------------------|
| Allergy Sufferers | Difficulty identifying hidden allergens | Builds a triple protection network of "personal allergens–environmental monitoring–alternative nutrition," integrating pollen count warnings |
| Diabetics | Precise balance between blood glucose and weight | Personalized "blood glucose–carbs–exercise" linkage model; high-sugar foods trigger compensatory recommendations |
| Extreme Obesity | Joint protection and gradual weight loss | Low-impact exercise + joint protection protocols, stepwise weight loss targets |
| Elderly with Obesity | Metabolic decline and comorbidity management | Dynamically lowers calorie targets (5% reduction per decade), fall-prevention exercise recommendations |
| Adolescents | Irreversible impact on growth and development | Sets minimum calorie thresholds; disables body image anxiety features; focuses on mental health |
| Postpartum Women | Dual challenges of lactation and metabolism | Dynamically adjusts caloric deficit based on milk production; recommends soothing exercises and psychological counseling |

### 4. Intelligent Psychological Companionship System

- **Affective Computing Module**: Integrates semantic analysis, tone recognition, and emotional feature extraction to detect negative language, anxious tones, and other signals.
- **Immediate Intervention**: Provides personalized psychological support and encouragement to prevent dropout.
- **Emotionally Engaging Interaction**: Elevates from "technical tool" to "holistic companion," enhancing user retention and long-term adherence.

### 5. Full-Chain Resource Integration Hub

Breaks down information silos to build a "Diet–Exercise–Health" trinity ecosystem:

- Real-time synchronization of authoritative dietary guidelines and personalized exercise tutorials.
- Automatically parses user dietary images and exercise data, transforming complex health knowledge into visual recommendations.
- Supports natural language retrieval of dietary records (e.g., "Find high-protein meals from last week").

### 6. Full-Cycle Health Management and Habit Formation

- **Lifelong Health Data Archive**: Deeply mines correlations among weight, body fat percentage, dietary intake, and other multi-dimensional data.
- **Trend Prediction**: Predicts health risks based on historical data; customizes stepwise weight loss plans.
- **Positive Reinforcement**: Daily/weekly/monthly/quarterly health reports, forming a "habit formation–positive reinforcement–continuous optimization" closed loop.

## Security and Privacy Design

- User health data encrypted with AES-256.
- All plugin calls are authenticated via the mcp-call_tool gateway, adhering to GDPR privacy protection standards.
- All operations involving user files are logged with audit trails.
- Model outputs undergo HTML escaping to prevent injection attacks.
- Sensitive data (e.g., allergens, disease information) is used exclusively for personalized computation and is not shared with third parties.

## Validation and Boundaries

### Completed Validation

- **Comparative Experiments**: For identical prepared food images, weight estimates from different large models and apps varied by nearly a factor of two, with calorie values differing by up to 3.4×; Healthy Food significantly reduced errors through interactive correction and reference-object methods.
- **Real-World Scenario Testing**: Correctly recognized an entire table of Chinese dishes (four items) in a single pass and automatically recommended sleep-aiding beverages based on the user's historical insomnia records.
- **Internal Benchmarks**: 92.3% accuracy on 79-category Chinese cuisine recognition; up to 12 ingredients recognized per image with confidence >85%.

### Current Boundaries

- Real-time video stream recognition is not yet supported.
- Special population modules require further validation with real-world clinical data.
- Long-term efficacy of the psychological companionship system has not been tested via randomized controlled trials.
- Relies on third-party large model APIs; service stability is subject to vendor availability.
- Not yet open-sourced; core algorithmic details are not fully disclosed.

## Quick Access

Healthy Food offers multiple access paths:

- Web App: `https://websim.ai/p/x021220jsowb1735q_1u/12`
- Coze Agent: `https://www.coze.cn/store/agent/7479232738571108388?bot_id=true`
- Tencent Yuanqi: `https://yuanqi.tencent.com/webim/#/chat/gknyQu?appid=2092115911376038976`
- WeChat Official Account path is currently in debugging.
