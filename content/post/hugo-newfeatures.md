---
title: "Hugo new features"
author: "Yuchen Jin"
tags: ["MarkDown", "Hugo"]
date: 2019-04-14T01:20:29-05:00
slug: "hugo-newfeatures"
draft: true
---

In this part, we try to show some useful examples and new extensions that are added into this theme.

<!--more-->

# More examples

## Examples for wiki card

{{< wikicard "Norm-coercive mappings" "Coercive_function#Norm-coercive_mappings" >}}

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## Examples for equations

Note that too many equations in a page may lead the loading to be very slow.

This is a plain equation:

$$
x = {-b \pm \sqrt{b^2-4ac} \over 2a}.
$$

Note that this equation is in "display style", which is not the same as "inline style". An equation with inline style is like this: $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$.

This is a single line equation with number:

<div class="eq">
\begin{align} \label{dfdf}
x = {-b \pm \sqrt{b^2-4ac} \over 2a}.
\end{align}
</div>

Here we make a reference for this equation, $\eqref{dfdf}$.

This is a single line equation which is very long:

<div class="eq">
\begin{align}
    \rho = \frac{ \sum_k \left(x_k - \overline{x}\right) \left(y_k - \overline{y}\right) }{ \sqrt{ \sum_k \left(x_k - \overline{x}\right)^2 \sum_k \left(y_k - \overline{y}\right)^2 } } \cdot \frac{ \sum_k \left(x_k - \overline{x}\right) \left(y_k - \overline{y}\right) }{ \sqrt{ \sum_k \left(x_k - \overline{x}\right)^2 \sum_k \left(y_k - \overline{y}\right)^2 } } \cdot \frac{ \sum_k \left(x_k - \overline{x}\right) \left(y_k - \overline{y}\right) }{ \sqrt{ \sum_k \left(x_k - \overline{x}\right)^2 \sum_k \left(y_k - \overline{y}\right)^2 } },
\end{align}
</div>

This is a multi-line equation:

<div class="eq">
\begin{equation}
    \begin{aligned}
        \mathcal{L}(\mathbf{A},~\boldsymbol{\theta}) &= \sum_k ( \mathbf{y}_k - \mathbf{A} \mathbf{x}_k - \boldsymbol{\theta} )^T ( \mathbf{y}_k - \mathbf{A} \mathbf{x}_k - \boldsymbol{\theta} )\\
        &= \sum_k \left[ \mathbf{y}_k^T\mathbf{y}_k + \mathbf{x}_k^T \mathbf{A}^T\mathbf{A} \mathbf{x}_k + \boldsymbol{\theta}^T \boldsymbol{\theta} + 2 \boldsymbol{\theta}^T \mathbf{A} \mathbf{x}_k - 2 \mathbf{y}_k^T \mathbf{A} \mathbf{x}_k - 2 \mathbf{y}_k^T \boldsymbol{\theta} \right].
    \end{aligned}
\end{equation}
</div>

Refer a multi-line equation is very trick, you could do this by [$(3)$](#mjx-eqn-3), the short code is:

```markdown
[$(3)$](#mjx-eqn-3)
```

where we use `3` to get the equation with number 3.

This is a matrix example:

<div class="eq">
\begin{equation}
  \begin{aligned}
    \mathbf{z} = \begin{bmatrix}
      \mathbf{z}_E \succ 0\\
      \mathbf{z}_S = 0
    \end{bmatrix} && \mathrm{and} &&
    \left\{
    \begin{matrix}
      \mathbf{H_E x} = \mathbf{h}_E, \\
      \mathbf{H_S x} \succ \mathbf{h}_S.
    \end{matrix}
    \right.
  \end{aligned}
\end{equation}
</div>

This is another matrix example:

<div class="eq">
\begin{equation}
  \begin{aligned}
    \mathbf{H}_E \mathbf{m} =
    \begin{bmatrix}
      1 & 0 & 0 & 0 & 0 & \cdots & 0 \\
      0 & 1 & 0 & 0 & 0 & \cdots & 0 \\
      0 & 0 & 1 & 0 & 0 & \cdots & 0 \\
      \vdots & \vdots & \vdots & \vdots & \vdots & \ddots & \vdots \\
      0 & 0 & 0 & \cdots & 1 & \cdots & 0
    \end{bmatrix}_{P_E \times N}
    \mathbf{m} = \begin{bmatrix}
      m_{E1} \\
      m_{E2} \\
      m_{E3} \\
      \cdots \\
      m_{EP_E}
    \end{bmatrix} = \mathbf{m}_E = \mathbf{0}.
  \end{aligned}
\end{equation}
</div>

# More extensions

## Show pdf

This is a pdf viewer.

{{< docs "./sample.pdf" >}}

## Plotly

Plotly is a powerful tool for drawing interactive figures. Users could check [here][plotly] to see the documentation of this library. Here we show an example of a 3D surface plot. Note that in a page there should be no more than 12 plots. If exceeding, the extra plots could not be loaded.

<div class="plotlycanvas", style="width:90%; max-width:750px">
  <div class="plotlytitle", style="width:730px">Comparison between the interpolated Jaccard index and original one.</div>
  <div id="lovasz-comp-11-ent", style="width:750px"></div>
</div>

## Mermaid

Mermaid is an drawing tool for flowchart, gantt chart and sequence diagram. Users could check [here][mermaid] to see the documentation of this library. Here we show an example of a flow chart.

<div class="mermaid">
graph TB
    c1-->a2
    subgraph one
    a1-->a2
    end
    subgraph two
    b1-->b2
    end
    subgraph three
    c1-->c2
    end
</div>

<script>
Plotly.d3.csv('./lovasz-comp-11-ent.csv', function(err, rows){
function unpack(rows, key) {
  return rows.map(function(row) { return row[key]; });
}
  
var z1_data=[ ]
var z2_data=[ ]
var x_data=[ ]
var y_data=[ ]
for(i=0;i<50;i++)
{
  z1_data.push(unpack(rows,i));
}
for(i=50;i<100;i++)
{
  z2_data.push(unpack(rows,i));
}
for(i=100;i<150;i++)
{
  x_data.push(unpack(rows,i));
}
for(i=150;i<200;i++)
{
  y_data.push(unpack(rows,i));
}
var data1 = {
  x: x_data,
  y: y_data,
  z: z1_data,
  type: 'surface',
  colorscale: 'Viridis',
  scene: "scene1"
};
var data2 = {
  x: x_data,
  y: y_data,
  z: z2_data,
  type: 'surface',
  colorscale: 'Viridis',
  scene: "scene2"
};
  
var layout = {
  autosize: true,
  scene1: {
    xaxis:{title: 'y1'},
    yaxis:{title: 'y2'},
    zaxis:{title: 'J'},
    domain: {
        x: [0.0,  0.46],
        y: [0.0, 1.0]
    },
    aspectmode: 'manual',
    aspectratio: {
      x: 1,
      y: 1,
      z: 1
    },
    camera:{
      eye:{
        x:-1.25,
        y:-1.25,
        z:1.25
      }
    }
  },
  scene2: {
    xaxis:{title: 'y1'},
    yaxis:{title: 'y2'},
    zaxis:{title: 'J'},
    domain: {
        x: [0.54,  1.0],
        y: [0.0, 1.0]
    },
    aspectmode: 'manual',
    aspectratio: {
      x: 1,
      y: 1,
      z: 1
    },
    camera:{
      eye:{
        x:-1.25,
        y:-1.25,
        z:1.25
      }
    }
  },
  margin: {
    l: 45,
    r: 30,
    b: 45,
    t: 30,
  }
};
Plotly.newPlot('lovasz-comp-11-ent', [data1, data2], layout);
});
</script>

[plotly]:https://plot.ly/javascript/
[mermaid]:https://mermaidjs.github.io/