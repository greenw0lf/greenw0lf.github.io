+++
title = "Projects"
+++

## Work-related projects

### OH-SMArt

**O**ral **H**istory - **S**tories at the **M**useum around **Art**works (**OH-SMArt**) is a long term initiative to significantly improve the digital research chain around using Oral History and spoken narratives, with research into artworks and museums as a use case. My role within this project is to evaluate state-of-the-art speech recognition models such as Whisper and XLS-R by creating benchmarks with various metrics such as Word Error Rate (WER), time it takes to evaluate a subset, and memory usage. Based on the benchmark results, I then propose and implement one of the models as an automatic transcriber within the infrastructure of the Sound & Vision Institute which can be used as a tool by researchers working with digital media archives to automatically transcribe Oral History interviews or other audiovisual content present in the Institute's digital archive.

The model which performed the best in the benchmarks is Whisper large-v2 with Voice Activity Detection (VAD). Additionally, the implementation of Whisper used for the tool is [faster-whisper](https://github.com/SYSTRAN/faster-whisper). **The benchmark results** can be found in the **project below**.

The resulting tool can be found here: https://github.com/beeldengeluid/whisper-asr-worker.

### Dutch Open Speech Recognition Benchmark (DOSRB)

While doing the evaluation via benchmarking for the OH-SMArt project, my supervisors and I thought of an initiative to disseminate these results that would also involve external parties. The initiative that resulted is called Dutch Open Speech Recognition Benchmark (DOSRB) and it is a joint effort done in collaboration with Stichting Open Spraaktechnologie (Open Speech Technology Foundation). DOSRB is open-source and the goal is for it to be driven by the community, inviting every researcher, company, or developer of Dutch Speech Recognition technology to contribute, whether it be by adding their results and experimental setups or through suggestions for improvement of the structure or the presentation. We hope that the Dutch Open Speech Recognition Benchmark will enhance the existing Dutch ASR Benchmark landscape, with a particular emphasis on promoting replicability, transparency, and accessibility.

The official website that hosts DOSRB can be found here: https://opensource-spraakherkenning-nl.github.io/ASR_NL_results/. Results of the initial benchmark can be found under *"UT's benchmark"*, whereas the benchmark that compares different implementations of Whisper, such as the [original implementation from OpenAI](https://github.com/openai/whisper), [WhisperX](https://github.com/m-bain/whisperX), or [faster-whisper](https://github.com/SYSTRAN/faster-whisper), can be found under *"NISV's Whisper benchmark"*.

### Contribution: ASR_NL_benchmark

A tool that I often used for conducting the evaluations is [ASR_NL_benchmark](https://github.com/opensource-spraakherkenning-nl/ASR_NL_benchmark). The description, as seen on the Github page, is the following:

"ASR-NL-benchmark is a python package to evaluate and compare the performance of speech-to-text for the Dutch language. Universities and Dutch media companies joined forces to develop this package that makes it easier to compare the performance of various open-source or commercial speech-to-text solutions on Dutch broadcast media. This package wraps around the famous sclite tool (part of SCTK that has been used for decades in the speech-to-text benchmark evaluations organised by NIST in the US). Further, the package contains several preprocessing files and connectors to databases."

My main contributions to this tool include:
- adding more variations of words (e.g. 'k => ik; 'r => er)
- improving the normalization of numbers. By normalization of numbers I mean writing the numbers out (20 => twintig)
- adding some test files
- adding the ability to skip normalization for the reference/hypothesis files (or both)
- adding back punctuation that was removed before (' and -)
- option to output a more detailed breakdown of the alignment of the reference-hypothesis files
- overall increasing the readability of the README

## Personal project

### Telegram Bot Transcriber

Together with a friend from university, we developed a small bot for the instant messaging app Telegram that can be added to a group chat and will transcribe any type of message that contains audio in it ([voice/video] [messages/files]). This was done for personal use mainly, to transcribe voice messages in our friend group chat.

It can be run in 2 ways:
1. `Python` faster-whisper backend + `Rust` Telegram Bot/API frontend (only supports voice messages)
2. Full `Python` Bot, using `python-telegram-bot` for communicating with the API (supports all types of formats, check `full_python_bot/README` for more details)

Link: https://github.com/AntoniosBarotsis/telegram-transcriber

## Study-related projects

### Talking Clock

This is a project developed for an assignment of the course "Introduction to Voice Technology", as part of my Master, together with a classmate. It is a fun little project that is based on the idea of concatenative speech synthesis (using multiple prerecorded audio segments and combining them together based on some predefined logic).

The clock can say the current time in Romanian, Irish, Polish, and French. It also has a speed adjust feature if you want to hear the time at a faster/slower rate. Rules of telling time for each language can also be found in the `README`. I wanted to work more on it and add features such as male/female voice selection or TTS/concatenative speech synthesis, but for now I am quite busy with my main job.

Link: https://github.com/greenw0lf/talking-clock

### License Plate Recognizer

This project was developed for the course "Image Processing" of my 2nd year of Bachelor, together with a classmate. It involves basic image processing techniques, such as color ranges, masking through kernel convolution, contour finding, OCR matching, and for me it was the gateway project to the world of multimedia processing. The pipeline was simple:
- Select several frames from a video that contain the same license plate
- Within each frame, localize and isolate the license plate from the rest of the image
- Convert each frame into black and white in such a way that the characters are isolated from the background
- Segment the license plate into the separate characters
- Match each character to a database of characters available using a similarity metric to find the most likely character + Dutch license plate format rules
- Compile the final text matching the full license plate
- After processing each selected frame of the same license plate, conduct a majority vote to find the most likely license plate

Unfortunately, the code is not publicly available as I want to avoid the risk of current Image Processing students to find it and use (parts of) it as their own, thus plagiarizing the project. However, I am mentioning it as it was a stressful but very educational experience.
