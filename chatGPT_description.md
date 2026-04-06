# Slanted-edge MTF50 measurement (revised core methods text)

Spatial frequency performance was quantified by slanted-edge analysis of a high-contrast edge target imaged with a custom 1x macro-imaging system (M Plan Apo 2x objective, Mitutoyo; LP126CU/M camera and TTL100-A tube lens, Thorlabs). The pixel and Rayleigh resolutions of the system are calculated to be 3.45 µm/pixel and 3.40 µm (at 587.6 nm), respectively. The edge target was recorded at an oblique angle relative to the detector grid to provide sub-pixel phase diversity. Exposure time was adjusted to avoid saturation and then held constant across samples within each comparison set. To minimize bias from camera-internal processing, analysis used raw sensor 12-bit data.

In this study, moduletion transfer function (MTF) was not used primarily to benchmark the intrinsic resolution of the imaging hardware itself. Rather, it was used as a comparative readout of how strongly a tissue specimen degraded contrast transfer after tissue clearing. Specifically, MTF measured from the bare high-contrast target was compared with MTF measured when a cleared tissue sample was placed over the same target, and the reduction in MTF50 (see description below) was interpreted as a relative proxy for residual blur, scattering, and contrast attenuation introduced by the tissue. Under matched imaging conditions, this approach also enabled semi-quantitative comparison of different tissue-clearing protocols.

Within each image, a rectangular region of interest (ROI) spanning the edge transition and adjacent background was selected after excluding clipped pixels. The edge orientation and intercept were estimated in the ROI, and each pixel center was projected onto the axis normal to the fitted edge. Intensities were then re-binned by signed edge-normal distance to reconstruct an oversampled edge spread function (ESF), \(E(d)\), at sub-pixel spacing, where \(d\) denotes signed distance along the edge-normal axis and \(f\) denotes spatial frequency.

## Principle

For a linear, approximately shift-invariant imaging system, the recorded image can be modeled as the convolution of the object intensity distribution with the system point spread function (PSF). When the object is an ideal step edge, the measured edge profile corresponds to the ESF. Differentiating that edge profile along the edge-normal direction yields the line spread function (LSF), which is the system response to a narrow line and is directly related to the PSF integrated along the edge direction. The Fourier transform of the LSF gives the one-dimensional optical transfer function (OTF) along the same axis, and the magnitude of the OTF, normalized at zero frequency, is the modulation transfer function (MTF). This is the mathematical basis for estimating spatial frequency response from the sequence ESF -> LSF -> OTF/MTF.

## Core equations

The ESF, LSF, OTF, and MTF were defined as

$$
\begin{aligned}
E(d) &= \text{edge spread function}, \\
L(d) &= \frac{\mathrm{d}E(d)}{\mathrm{d}d}, \\
\operatorname{OTF}(f) &= \mathcal{F}\{L(d)\}(f), \\
\operatorname{MTF}(f) &= \frac{\left| \operatorname{OTF}(f) \right|}{\left| \operatorname{OTF}(0) \right|}.
\end{aligned}
$$

To limit truncation artifacts and suppress amplification of high-frequency noise, \(L(d)\) was optionally multiplied by an apodization window before Fourier transformation. MTF50 was defined as the spatial frequency \(f_{50}\) satisfying

$$
\operatorname{MTF}(f_{50}) = 0.5,
$$

with \(f_{50}\) estimated by interpolation between adjacent sampled frequency bins.

Frequencies were first reported in cycles per pixel. Where required, values were converted to image-plane and object-plane line pairs per millimeter (lp/mm) as

$$
\begin{aligned}
f_{\mathrm{image}}^{(\mathrm{lp/mm})} &= \frac{f_{\mathrm{pixel}}^{(\mathrm{cy/pixel})}}{p}, \\
f_{\mathrm{object}}^{(\mathrm{lp/mm})} &= \frac{M\,f_{\mathrm{pixel}}^{(\mathrm{cy/pixel})}}{p},
\end{aligned}
$$

where \(p\) is the detector pixel pitch in mm/pixel and \(M\) is the system magnification.

Unless otherwise stated, all inter-condition comparisons used matched edge targets, acquisition settings, ROI definitions, preprocessing settings, and analysis parameters.

## Reporting notes for manuscript adaptation

- In sampled digital systems, edge-derived frequency curves are often denoted spatial frequency response (SFR); here, the conventional term MTF50 is retained for readability while preserving the edge-based definition above.
- Because this assay was used to compare tissue-dependent degradation rather than the isolated instrument limit, the manuscript should clearly distinguish system performance from sample-induced attenuation of contrast transfer.
- For reproducibility, report at minimum the edge angle, ROI size, oversampling or bin width, derivative method, window function, interpolation rule for MTF50, and whether demosaicing, sharpening, or nonlinear denoising were active.
- If optical blur, scattering, and sampling are discussed together, clarify whether the measured MTF reflects the full imaging chain, the sample plus imaging chain, or a partially isolated subsystem.

## References

1. ISO 12233:2017. *Photography - Electronic still picture imaging - Resolution and spatial frequency responses.* International Organization for Standardization.
2. Burns, P. D. (2000). Slanted-edge MTF for digital camera and scanner analysis. *Proc. PICS Conference*.
3. Williams, D. R. and Burns, P. D. (2001). Diagnostics for imaging system MTF from slanted-edge data. *Proc. SPIE*.
4. van den Bergh, F. et al. *Robust edge spread function construction methods to counter the effects of correlated noise.* (edge-based MTF/SFR methodology).
