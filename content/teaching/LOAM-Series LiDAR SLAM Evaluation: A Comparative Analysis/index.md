---
title: Loam-Series Evaluation
summary: Evaluation of comprehensive SLAM systems, namely Lego- LOAM and SC-LEGO-LOAM
date: 2023-11-24
type: docs
math: false
tags:
  - SLAM, LiDAR
image:
  caption: 'MulRAN Dataset'
---
## Introduction

In this project, we systematically examined and compared various algorithms within the LOAM series,
specifically ALOAM, LEGO-LOAM, and SC-LEGO-LOAM. Our primary focus was on meticulously analyzing the developmental
trajectory from a singular lidar odometry approach (the original LOAM) to the comprehensive SLAM systems, namely Lego-
LOAM and SC-LEGO-LOAM. This comprehensive analysis involved intricate comparisons between algorithms, elucidation
of improvements made, and in-depth assessments. Ultimately, we conducted thorough testing and comparison of these three
algorithms on two extensive long-distance datasets

## Evaluation and Metrics

**Table 1: ATE of LeGO-LOAM and SC-LeGO-LOAM in Kaist sequence** 

$$
\begin{array}{|l|c|c|}
\hline
\textbf{Metric} & \textbf{SC-LeGO-LOAM (\%)} & \textbf{LeGO-LOAM (\%)} \\ \hline
\text{max} & 1.60 & 2.55 \\ \hline
\text{mean} & 0.84 & 1.03 \\ \hline
\text{median} & 0.82 & 1.01 \\ \hline
\text{min} & 0.08 & 1.35 \\ \hline
\text{rmse} & 0.90 & 1.13 \\ \hline
\end{array}
$$


**Table 2: ATE of LeGO-LOAM and SC-LeGO-LOAM in Riverside sequence**

$$
\begin{array}{|l|c|c|}
\hline
\textbf{Metric} & \textbf{SC-LeGO-LOAM (\%)} & \textbf{LeGO-LOAM (\%)} \\ \hline
\text{max} & 2.89 & 8.55 \\ \hline
\text{mean} & 1.35 & 2.82 \\ \hline
\text{median} & 1.36 & 3.34 \\ \hline
\text{min} & 0.20 & 0.27 \\ \hline
\text{rmse} & 1.46 & 3.34 \\ \hline
\end{array}
$$
![RIVERSIDE03](https://github.com/rahil-bhowal007/LOAM-SERIES/assets/65888130/29b68ae0-8bc3-4e0c-ba96-7ac997c3e8a0)
<p align="center">
<it> Fig 1. Point Cloud Comparison on RIVERSIDE 03 Dataset </it>
</p>

![KAIST 01 ](https://github.com/rahil-bhowal007/LOAM-SERIES/assets/65888130/85627c42-4458-417a-80fc-0358b5816f09)
<p align="center">
<it>Fig 2. Point Cloud Comparison on KAIST 01 Dataset</it>
</p>
The mapping results of three algorithms on the Kaist dataset
are illustrated in Figure 1 and Figure 2.
<br/>

![loam_r](https://github.com/rahil-bhowal007/LOAM-SERIES/assets/65888130/722af654-f017-4750-ac2d-bf487ee78049)
<p align="center">
<it>Fig 3. LOAM on RIVERSIDE Dataset</it>
</p>

![legoloam_r(1)](https://github.com/rahil-bhowal007/LOAM-SERIES/assets/65888130/cdb7b46f-955d-4133-a3d5-6392c195d703)
<p align="center">
<it>Fig 4. LeGO-LOAM on RIVERSIDE Dataset</it>
</p>

![sclegoloam_r](https://github.com/rahil-bhowal007/LOAM-SERIES/assets/65888130/dcb8988a-5100-4975-b179-f6cc25bdec66)
<p align="center">
<it>Fig 5. SC-LeGO-LOAM on RIVERSIDE Dataset</it>





## Output

**Map**
Here are the map formed by the LOAM Algorithm on the MulRAN Dataset(KAIST track):
{{< youtube Ytw8goT86MY >}}


**Youtube**:

    {{</* youtube w7Ft2ymGmfc */>}}

**Bilibili**:

    {{</* bilibili id="BV1WV4y1r7DF" */>}}

**Video file**

Videos may be added to a page by either placing them in your `assets/media/` media library or in your [page's folder](https://gohugo.io/content-management/page-bundles/), and then embedding them with the _video_ shortcode:

    {{</* video src="my_video.mp4" controls="yes" */>}}

## Podcast

You can add a podcast or music to a page by placing the MP3 file in the page's folder or the media library folder and then embedding the audio on your page with the _audio_ shortcode:

    {{</* audio src="ambient-piano.mp3" */>}}

Try it out:

{{< audio src="ambient-piano.mp3" >}}

## Test students

Provide a simple yet fun self-assessment by revealing the solutions to challenges with the `spoiler` shortcode:

```markdown
{{</* spoiler text="👉 Click to view the solution" */>}}
You found me!
{{</* /spoiler */>}}
```

renders as

{{< spoiler text="👉 Click to view the solution" >}} You found me 🎉 {{< /spoiler >}}

## Math

Hugo Blox Builder supports a Markdown extension for $\LaTeX$ math. You can enable this feature by toggling the `math` option in your `config/_default/params.yaml` file.

To render _inline_ or _block_ math, wrap your LaTeX math with `{{</* math */>}}$...${{</* /math */>}}` or `{{</* math */>}}$$...$${{</* /math */>}}`, respectively.

{{% callout note %}}
We wrap the LaTeX math in the Hugo Blox _math_ shortcode to prevent Hugo rendering our math as Markdown.
{{% /callout %}}

Example **math block**:

```latex
{{</* math */>}}
$$
\gamma_{n} = \frac{ \left | \left (\mathbf x_{n} - \mathbf x_{n-1} \right )^T \left [\nabla F (\mathbf x_{n}) - \nabla F (\mathbf x_{n-1}) \right ] \right |}{\left \|\nabla F(\mathbf{x}_{n}) - \nabla F(\mathbf{x}_{n-1}) \right \|^2}
$$
{{</* /math */>}}
```

renders as

{{< math >}}
$$\gamma_{n} = \frac{ \left | \left (\mathbf x_{n} - \mathbf x_{n-1} \right )^T \left [\nabla F (\mathbf x_{n}) - \nabla F (\mathbf x_{n-1}) \right ] \right |}{\left \|\nabla F(\mathbf{x}_{n}) - \nabla F(\mathbf{x}_{n-1}) \right \|^2}$$
{{< /math >}}

Example **inline math** `{{</* math */>}}$\nabla F(\mathbf{x}_{n})${{</* /math */>}}` renders as {{< math >}}$\nabla F(\mathbf{x}_{n})${{< /math >}}.

Example **multi-line math** using the math linebreak (`\\`):

```latex
{{</* math */>}}
$$f(k;p_{0}^{*}) = \begin{cases}p_{0}^{*} & \text{if }k=1, \\
1-p_{0}^{*} & \text{if }k=0.\end{cases}$$
{{</* /math */>}}
```

renders as

{{< math >}}

$$
f(k;p_{0}^{*}) = \begin{cases}p_{0}^{*} & \text{if }k=1, \\
1-p_{0}^{*} & \text{if }k=0.\end{cases}
$$

{{< /math >}}

## Code

Hugo Blox Builder utilises Hugo's Markdown extension for highlighting code syntax. The code theme can be selected in the `config/_default/params.yaml` file.


    ```python
    import pandas as pd
    data = pd.read_csv("data.csv")
    data.head()
    ```

renders as

```python
import pandas as pd
data = pd.read_csv("data.csv")
data.head()
```

## Inline Images

```go
{{</* icon name="python" */>}} Python
```

renders as

{{< icon name="python" >}} Python

## Did you find this page helpful? Consider sharing it 🙌
