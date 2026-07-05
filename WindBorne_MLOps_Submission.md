# WindBorne Systems — Machine Learning Operations Engineer

## Application Challenge Submission

**Aarush Narang** | aarushnarang@arizona.edu | [aarush.work](https://aarush.work) | [GitHub](https://github.com/aarushnarang02/)

---

### 1. Describe the most complex ML model inference you have run.

A real-time collision risk pipeline for traffic video: YOLO11 detection feeding multi-object tracking, then trajectory risk scoring, every frame on live feeds. The model was the easy part. Profiling showed pre/postprocessing, not the network, was the bottleneck; TensorRT conversion plus fixing that took it from 12 to 46 FPS, validated over 12 hours of footage and 40,000+ tracked road users.

### 2. What's the most pain you've faced running production systems? What's an interesting change you made to increase resilience or uptime?

Serving my chest X-ray triage model: GPU inference was too costly to keep warm, and broken model exports failed silently. I moved to ONNX for 4x faster CPU inference (~120 ms/image) so it runs on Cloud Run and scales to zero safely, then made CI run real images through the exported model before every deploy, so a bad build fails the pipeline, not production. Prometheus metrics watch the rest.
