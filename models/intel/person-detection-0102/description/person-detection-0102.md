# person-detection-0102

## Use Case and High-Level Description

This is a person detector that is based on MobileNetV2
backbone with two SSD heads from 1/16 and 1/8 scale feature maps and clustered
prior boxes for 512x512 resolution.

## Example

![](./person-detection-0102.png)

## Specification

| Metric                          | Value                                     |
|---------------------------------|-------------------------------------------|
| AP                              | 91.21% (internal test set)                |
| Pose coverage                   | Standing upright, parallel to image plane |
| Support of occluded persons     | YES                                       |
| Occlusion coverage              | <50%                                      |
| Min person height               | 100 pixels (on 1080p)                     |
| GFlops                          | 3.143                                     |
| MParams                         | 1.817                                     |
| Source framework                | PyTorch\*                                 |

Average Precision (AP) is defined as an area under
the [precision/recall](https://en.wikipedia.org/wiki/Precision_and_recall)
curve. Intersection over union threshold of 0.5 is used for matching.

## Performance

## Inputs

Name: `input`, shape: [1x3x512x512] - An input image in the format [BxCxHxW],
where:

- B - batch size
- C - number of channels
- H - image height
- W - image width

Expected color order is BGR.

## Outputs

The net outputs blob with shape: [1, 1, N, 7], where N is the number of detected
bounding boxes. Each detection has the format
  [`image_id`, `label`, `conf`, `x_min`, `y_min`, `x_max`, `y_max`], where:
  - `image_id` - ID of the image in the batch
  - `label` - predicted class ID
  - `conf` - confidence for the predicted class
  - (`x_min`, `y_min`) - coordinates of the top left bounding box corner
  - (`x_max`, `y_max`) - coordinates of the bottom right bounding box corner.

## Legal Information
[*] Other names and brands may be claimed as the property of others.
