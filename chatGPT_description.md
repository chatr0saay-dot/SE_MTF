# Slanted-edge MTF50 measurement (revised draft)

Spatial resolution was quantified using slanted-edge analysis under matched acquisition settings for all samples. A high-contrast straight edge was imaged at a small oblique angle to the detector grid to provide sub-pixel phase diversity. To minimize algorithmic bias, we analyzed raw sensor data or linear 16-bit renders derived from raw data (that is, without tone mapping, edge enhancement, or nonlinear denoising when avoidable).

Within each image, we selected a rectangular ROI spanning the edge transition and adjacent background while excluding clipped pixels. The edge orientation and intercept were estimated in the ROI, and each pixel center was projected onto the axis normal to the fitted edge. Intensities were then re-binned by signed edge-normal distance to reconstruct an oversampled edge spread function (ESF), \(E(d)\), at sub-pixel spacing.

The line spread function (LSF) was obtained from the ESF derivative,
\[
L(d)=\frac{dE(d)}{dd},
\]
followed by optional windowing of \(L(d)\) before Fourier analysis to limit truncation artifacts and reduce high-frequency noise amplification. The normalized modulation transfer function was computed as
\[
\mathrm{MTF}(f)=\frac{\left|\mathcal{F}\{L(d)\}(f)\right|}{\left|\mathcal{F}\{L(d)\}(0)\right|},
\]
where \(f\) is spatial frequency and \(\mathcal{F}\{\cdot\}\) denotes the Fourier transform. MTF50 was defined as the frequency at which \(\mathrm{MTF}(f)=0.5\), estimated by interpolation between adjacent sampled frequencies.

Frequencies were first reported in cycles/pixel. When needed, we converted to image-plane line pairs per millimeter (lp/mm) using detector pixel pitch \(p\) (mm/pixel):
\[
\mathrm{lp/mm}=\frac{f}{p}.
\]
For object-space reporting (for example, microscopy), image-plane frequency was scaled by system magnification \(M\):
\[
(\mathrm{lp/mm})_{\mathrm{object}}=\frac{fM}{p}.
\]
Unless noted otherwise, all inter-condition comparisons used matched edge targets, ROI definitions, preprocessing settings, and analysis parameters.

## Reporting notes for biomedical manuscripts

- In sampled digital systems, edge-derived frequency curves are often denoted SFR; we use the common term MTF50 for readability while keeping the edge-based definition above.
- To support reproducibility, report at minimum: edge angle, ROI size, oversampling/bin width, derivative method, window function, interpolation rule for MTF50, and whether demosaicing/sharpening/noise reduction were active.
- If optical blur and sampling are jointly discussed, clarify whether MTF refers to the full system response (optics + detector + processing) or an isolated subsystem.

## Key references

1. ISO 12233:2017. *Photography — Electronic still picture imaging — Resolution and spatial frequency responses.* International Organization for Standardization.
2. Burns, P. D. (2000). Slanted-edge MTF for digital camera and scanner analysis. *Proc. PICS Conference*.
3. Williams, D. R. & Burns, P. D. (2001). Diagnostics for imaging system MTF from slanted-edge data. *Proc. SPIE*.
