## 不同的图片的编码格式的区别

图片的编码格式一般有png、jpg、jpeg、GIF和webp等几种格式，不同格式之间的有不同的优缺点以及适用场景。

图片的格式分类有以下几种：

- 无压缩。无压缩的图片格式不对图片数据进行压缩处理，能准确地呈现原图片，BMP格式的图片就是其中之一。
- 无损压缩：压缩算法对图片中所有的数据进行编码压缩，能在保证图片质量的同时降低图片的尺寸，png就是其中的代表。
- 有损压缩。压缩算法不会对图片中所有的数据进行编码压缩，而是在压缩的时候，去除了人言无法识别的图片细节。因此有损压缩可以再同等图片质量的情况下大幅度降低图片的尺寸，其中的代表方式就是jpg

1. jpg

    jpg是一种有损的基于直接色的图片格式。由于采用直接色，jpg可以表示的颜色有1600w之多，而人眼识别的颜色大约只有1W多。因此jpg适合将图片色彩丰富、渐变色多的图片。jpd有损压缩之后，图片的尺寸大幅度减小。但是jpg格式的图片不适于icon、logo等。相比png-8，在文件大小上没有任何优势。

2. png-8

    png-8采用无损压缩方式，基于8位所银色的位图格式。png-8相比gif对透明的支持更好，同等质量下，尺寸也更小。

3. png-24

    这种压缩方式采用无损压缩，是基于直接色的位图格式，png-24的图片质量堪比bmp，但是却又bmp不具备的尺寸优势。相比jpg、gif、png-8，尺寸上还是要大一些，正是因为高品质，无损压缩，非常适用于源文件或需要二次编辑的图片格式的保存。

    png-24与jpg一样能表达丰富的图片细节，但是并不梦替代jpg格式的图片，图片存储为png-24比存储为jpg，文件大小至少是jpg的五倍，但在图片质量上的提升却比较有限。除非对于品质的要求非常高，否则色彩丰富的网络图片还是推荐使用jpg。