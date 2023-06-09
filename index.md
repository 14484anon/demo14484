
## P-Flow: A Fast and Data-Efficient Zero-Shot TTS through Speech Prompting


### Abstract

While recent large-scale neural codec language models have shown significant improvement in zero-shot TTS by training on thousands of hours of data, they suffer from drawbacks such as a lack of robustness, slow sampling speed similar to previous autoregressive TTS methods, and reliance on pre-trained neural codec representations. Our work proposes P-Flow, a fast and data-efficient zero-shot TTS model that uses speech prompts for speaker adaptation. P-Flow comprises a speech-prompted text encoder for speaker adaptation and a flow matching generative decoder for high-quality and fast speech synthesis. Our speech-prompted text encoder uses speech prompts and text input to generate speaker-conditional text representation. The flow matching generative decoder uses the speaker-conditional output to synthesize high-quality personalized speech significantly faster than in real-time. Unlike the neural codec language models, we specifically train P-Flow on LibriTTS dataset using a continuous mel-representation. Through our training method using continuous speech prompts, P-Flow matches the speaker similarity performance of the large-scale zero-shot TTS models with two orders of magnitude less training data and has more than 20x faster sampling speed. Our results show that P-Flow has better pronunciation and is preferred in human likeness and speaker similarity to its recent state-of-the-art counterparts, thus defining P-Flow as an attractive and desirable alternative.


### Prompting v.s. Separate Speaker Encoder (Section 4.1)

* P-Flow: Use Speech-prompted text encoder
* P-Flow (w/o Prompt): Use a fixed-size speaker embedding from a transformer-based speech encoder

<table>
   <thead>
      <tr>
      <th style="text-align: center">Text</th>
         <th style="text-align: center">Reference</th>
         <th style="text-align: center">P-Flow </th>
         <th style="text-align: center">P-Flow  <br /> (w/o Prompt)</th>
      </tr>
   </thead>
   <tbody>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">They moved thereafter cautiously about the hut, groping before and about them to find something to show that Warrenton had fulfilled his mission.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/1_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/1_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/1_baseline.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Yea, his honourable worship is within. But he hath a godly minister or two with him, and likewise a leech.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/2_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/2_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/2_baseline.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">The army found the people in poverty and left them in comparative wealth.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/3_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/3_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/3_baseline.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">He was in deep converse with the clerk, and entered the hall holding him by the arm.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/4_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/4_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_1/4_baseline.wav" type="audio/wav"></audio></td>
      </tr>
   </tbody>
</table>


### Model Comparison (Section 4.2)
<table>
   <thead>
      <tr>
      <th style="text-align: center">Text</th>
         <th style="text-align: center">GT</th>
         <th style="text-align: center">Reference</th>
         <th style="text-align: center">P-Flow</th>
         <th style="text-align: center">VALL-E</th>
      </tr>
   </thead>
   <tbody>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">They moved thereafter cautiously about the hut, groping before and about them to find something to show that Warrenton had fulfilled his mission.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/1_gt.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/1_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/1_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/1_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">And lay me down in thy cold bed, and leave my shining lot.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/2_gt.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/2_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/2_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/2_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Yea, his honourable worship is within. But he hath a godly minister or two with him, and likewise a leech.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/3_gt.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/3_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/3_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/3_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Instead of shoes, the old man wore boots with turnover tops, and his blue coat had wide cuffs of gold braid.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/4_gt.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/4_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/4_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/4_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">The army found the people in poverty and left them in comparative wealth.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/5_gt.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/5_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/5_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/5_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Thus did this humane and right-minded father comfort his unhappy daughter; and her mother, embracing her again, did all she could to soothe her feelings.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/6_gt.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/6_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/6_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/6_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">He was in deep converse with the clerk, and entered the hall holding him by the arm.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/7_gt.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/7_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/7_pflow.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_2/7_valle.wav" type="audio/wav"></audio></td>
      </tr>
   </tbody>
</table>

### Effect of Guidance Scale and Euler Steps (Section 4.3)
#### Guidance Scale gamma (N=10)
<table>
   <thead>
      <tr>
      <th style="text-align: center">Text</th>
         <th style="text-align: center">Reference</th>
      <th style="text-align: center">P-Flow <br />(gamma=0) </th>
         <th style="text-align: center">P-Flow <br />(gamma=1) </th>
      <th style="text-align: center">P-Flow <br />(gamma=2) </th>
      </tr>
   </thead>
   <tbody>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">They moved thereafter cautiously about the hut, groping before and about them to find something to show that Warrenton had fulfilled his mission.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/1_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/1_pflow_g0.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/1_pflow_g1.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/1_pflow_g2.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Yea, his honourable worship is within. But he hath a godly minister or two with him, and likewise a leech.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/2_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/2_pflow_g0.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/2_pflow_g1.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/2_pflow_g2.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">The army found the people in poverty and left them in comparative wealth.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/3_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/3_pflow_g0.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/3_pflow_g1.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/3_pflow_g2.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">He was in deep converse with the clerk, and entered the hall holding him by the arm.</td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/4_reference.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/4_pflow_g0.wav" type="audio/wav"></audio></td>
         <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/4_pflow_g1.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_1/4_pflow_g2.wav" type="audio/wav"></audio></td>
      </tr>
   </tbody>
</table>

#### Number of Euler Steps N (gamma=1)
<table>
   <thead>
      <tr>
      <th style="text-align: center">Text</th>
         <th style="text-align: center">Reference</th>
      <th style="text-align: center">P-Flow <br />(N=1) </th>
         <th style="text-align: center">P-Flow <br />(N=2) </th>
      <th style="text-align: center">P-Flow <br />(N=5) </th>
      <th style="text-align: center">P-Flow <br />(N=10) </th>
      <th style="text-align: center">P-Flow <br />(N=20) </th>
      </tr>
   </thead>
   <tbody>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">They moved thereafter cautiously about the hut, groping before and about them to find something to show that Warrenton had fulfilled his mission.</td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/1_reference.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/1_pflow_n1.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/1_pflow_n2.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/1_pflow_n5.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/1_pflow_n10.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/1_pflow_n20.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Yea, his honourable worship is within. But he hath a godly minister or two with him, and likewise a leech.</td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/2_reference.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/2_pflow_n1.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/2_pflow_n2.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/2_pflow_n5.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/2_pflow_n10.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/2_pflow_n20.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">The army found the people in poverty and left them in comparative wealth.</td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/3_reference.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/3_pflow_n1.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/3_pflow_n2.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/3_pflow_n5.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/3_pflow_n10.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/3_pflow_n20.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">He was in deep converse with the clerk, and entered the hall holding him by the arm.</td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/4_reference.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/4_pflow_n1.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/4_pflow_n2.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/4_pflow_n5.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/4_pflow_n10.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/section4_3_2/4_pflow_n20.wav" type="audio/wav"></audio></td>
      </tr>
   </tbody>
</table>

### Zero-shot TTS with Emotional Reference Speech (Appendix)
Transcript: We have to reduce the number of plastic bags.
<table>
   <thead>
      <tr>
      <th style="text-align: center">Emotion</th>
      <th style="text-align: center">Reference</th>
      <th style="text-align: center">P-Flow</th>
      <th style="text-align: center">VALL-E</th>
      </tr>
   </thead>
   <tbody>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Anger</td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/1_reference.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/1_pflow.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/1_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Sleepiness</td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/2_reference.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/2_pflow.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/2_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Neutral</td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/3_reference.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/3_pflow.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/3_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Amused</td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/4_reference.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/4_pflow.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/4_valle.wav" type="audio/wav"></audio></td>
      </tr>
      <tr>
      <td style="text-align: left;vertical-align:middle;width: 420px;">Disgust</td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/5_reference.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/5_pflow.wav" type="audio/wav"></audio></td>
      <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/appendix/5_valle.wav" type="audio/wav"></audio></td>
      </tr>
   </tbody>
</table>
