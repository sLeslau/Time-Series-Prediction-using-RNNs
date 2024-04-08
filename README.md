
<h1 align="center">
  <br>
	Time-Series-Prediction-using-RNNs
  <br>
</h1>
  <h3 align="center">
    <a href="https://github.com/sLeslau">Shaked Leslau</a> •
    <a href="https://github.com/rishonadaniels">Rishona Daniels</a>

  </h3>
<h3 align="center">Final Project for Technion 046211 Deep Learning Course.

<h4 align="center">We compare various recurrent neural networks (RNNs) for prediction of dynamic and chaotic time series data. RNNs like long short-term memory (LSTM), gated recurrent unit (GRU) and transformers will be compared with each other and with a novel RNN method called reservoir computing</h4>

<p>See this paper for reference: https://github.com/quantinfo/ng-rc-paper-code/tree/master</hp>

<h4 align="center">
    <a href="https://colab.research.google.com/github/sLeslau/Time-Series-Prediction-using-RNNs"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
</h4>

# DDLP: Unsupervised Object-centric Video Prediction with Deep Dynamic Latent Particles


## DDLP - Evaluation

The evaluation protocol measures the reconstruction quality via 3 metrics: LPIPS, SSIM and PSNR.

We use the open-source `piqa` (`pip install piqa`) to compute the metrics. If `eval_im_metrics=True` in the config file,
the metrics will be computed every evaluation epoch on the *validation* set. The code saves the best model based
on the LPIPS metric.

To evaluate a pre-trained DDLP model (on the *test* set) on video prediction, we provide a script:

`python eval/eval_gen_metrics.py --help`

For example, to evaluate a model saved in `/310822_141959_obj3d128_ddlp` on the test set, with 6 conditional frames and a
generation horizon of 50 frames:

`python eval/eval_gen_metrics.py -d obj3d128 -p ./310822_141959_obj3d128 -c 6 --horizon 50`

The script will load the config file `hparams.json` from `/310822_141959_obj3d128_ddlp/hparams.json` and the model
checkpoint from `/310822_141959_obj3d128_ddlp/saves/obj3d128_ddlp_best_lpips.pth` and use it to generate video predictions.

Alternatively, you can specify a direct path to the checkpoint as follows:

`python eval/eval_gen_metrics.py -d obj3d128 -p ./checkpoints/ddlp-obj3d128 -c 6 --horizon 50 --checkpoint ./checkpoints/ddlp-obj3d128/obj3d128_ddlp.pth`

For more options, see `python eval/eval_gen_metrics.py --help`.

For a similar evaluation of DLPv2 in the single-image setting, see `eval_dlp_im_metric()` in `/eval/eval_gen_metrics.py`.

## DDLP - Video Prediction with Pre-trained Models

To generate a video prediction using a pre-trained model use `generate_ddlp_video_prediction.py` as follows:

`python generate_ddlp_video_prediciton.py -d obj3d128 -p ./310822_141959_obj3d128_ddlp -n 1 -c 10 --horizon 100`

The script will load the config file `hparams.json` from `/310822_141959_obj3d128_ddlp/hparams.json` and the model
checkpoint from `/310822_141959_obj3d128_ddlp/saves/obj3d128_ddlp_best_lpips.pth` and use it to generate `n` video predictions,
based on 10 conditional input frames, and a final video length of 100 frames. In the example above, a single (`n=1`) video
will be generated and saved within an `animations` directory (will be created if it doesn't exist) under the checkpoint directory.

Alternatively, you can specify a direct path to the checkpoint as follows:

`python generate_ddlp_video_prediciton.py -d obj3d128 -p ./checkpoints/ddlp-obj3d128 -n 1 -c 10 --horizon 100 --checkpoint ./checkpoints/ddlp-obj3d128/obj3d128_ddlp.pth`

For more options, see `python generate_ddlp_video_prediction.py --help`.


## Repository Organization

| File name                                            | Content                                                                                     |
|------------------------------------------------------|---------------------------------------------------------------------------------------------|
| `/notebooks`                                         | Jupyter Notebook implementations of the various models                                      |
| `environment.yml`                                    | Anaconda environment file to install the required dependencies                              |
