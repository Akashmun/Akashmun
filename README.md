- 👋 Hi, I’m @Akashmun
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Akashmun/Akashmun is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
export MODEL_DIR="/path/to/SeamlessExpressive/model"
export TEST_SET_TSV="input.tsv" # Your dataset in a TSV file, with headers "id", "audio"
export TGT_LANG="spa" # Target language to translate into, options including "fra", "deu", "eng" ("cmn" and "ita" are experimental)
export OUTPUT_DIR="tmp/" # Output directory for generated text/unit/waveform
export TGT_TEXT_COL="tgt_text" # The column in your ${TEST_SET_TSV} for reference target text to calcuate BLEU score. You can skip this argument.
export DFACTOR="1.0" # Duration factor for model inference to tune predicted duration (preddur=DFACTOR*preddur) per each position which affects output speech rate. Greater value means slower speech rate (default to 1.0). See expressive evaluation README for details on duration factor we used.
expressivity_evaluate ${TEST_SET_TSV} \
  --gated-model-dir ${MODEL_DIR} --task s2st --tgt_lang ${TGT_LANG} \
  --audio_root_dir "" --output_path ${OUTPUT_DIR} --ref_field ${TGT_TEXT_COL} \
  --model_name seamless_expressivity --vocoder_name vocoder_pretssel \
  --text_unk_blocking True --duration_factor ${DFACTOR}
