# Awesome Compression [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of awesome compression and decompression algorithms, libraries, tools, and resources.

Data compression is the process of encoding information using fewer bits than the original representation. It is a fundamental concept in computer science and information theory, enabling efficient storage and transmission of data.

## Contents

- [Theory and Basics](#theory-and-basics)
- [General Purpose Algorithms](#general-purpose-algorithms)
  - [Entropy Coding](#entropy-coding)
  - [Dictionary Coders](#dictionary-coders)
  - [Modern Algorithms](#modern-algorithms)
- [Integer and Database Compression](#integer-and-database-compression)
- [Neural Compression](#neural-compression)
- [Model Compression (ML Efficiency)](#model-compression-ml-efficiency)
- [Media Compression](#media-compression)
  - [Image](#image)
  - [Audio](#audio)
  - [Video](#video)
- [Specialized Compression](#specialized-compression)
- [Libraries and Tools](#libraries-and-tools)
- [Columnar and Big Data](#columnar-and-big-data)
- [Hardware Acceleration](#hardware-acceleration)
- [Benchmarking](#benchmarking)
- [Datasets and Corpora](#datasets-and-corpora)
- [Books](#books)
- [Seminal Papers](#seminal-papers)
- [Journals and Publications](#journals-and-publications)
- [Engineering Blogs](#engineering-blogs)
- [Blogs and Web Resources](#blogs-and-web-resources)
- [Courses and Tutorials](#courses-and-tutorials)
- [Visualizations and Demos](#visualizations-and-demos)
- [Community and Conferences](#community-and-conferences)

---

## Theory and Basics
*Foundational concepts in information theory and data compression.*

- [Information Theory (Shannon)](https://en.wikipedia.org/wiki/Information_theory) - The mathematical study of the quantification, storage, and communication of information.
- [Kolmogorov Complexity](https://en.wikipedia.org/wiki/Kolmogorov_complexity) - The length of the shortest computer program that produces the object as output.
- [Lossless vs. Lossy Compression](https://en.wikipedia.org/wiki/Data_compression) - The two main categories of data compression techniques.
- [Burrows-Wheeler Transform (BWT)](https://en.wikipedia.org/wiki/Burrows%E2%80%93Wheeler_transform) - A data transformation algorithm that rearranges a character string into runs of similar characters, useful for compression.
- [Move-to-Front Transform (MTF)](https://en.wikipedia.org/wiki/Move-to-front_transform) - An encoding of data designed to improve the performance of entropy encoding techniques.
- [Prediction by Partial Matching (PPM)](https://en.wikipedia.org/wiki/Prediction_by_partial_matching) - An adaptive statistical data compression technique based on context modeling and prediction.
- [Context Mixing](https://en.wikipedia.org/wiki/Context_mixing) - A type of data compression where predictions from multiple independent models are combined to estimate the probability of the next bit.
- [The Hitchhiker's Guide to Compression](https://github.com/encode/hitchhikers-guide-to-compression) - A comprehensive guide and repository of lossless compression algorithms.

## General Purpose Algorithms
*Algorithms used for lossless data compression, applicable to any data.*

### Entropy Coding
- [Huffman Coding](https://en.wikipedia.org/wiki/Huffman_coding) - An optimal prefix code commonly used for lossless data compression.
- [Arithmetic Coding](https://en.wikipedia.org/wiki/Arithmetic_coding) - A form of entropy encoding that encodes the entire message into a single number.
- [Asymmetric Numeral Systems (ANS)](https://en.wikipedia.org/wiki/Asymmetric_numeral_systems) - A family of entropy coding methods combining the ratio of Huffman coding with the performance of arithmetic coding.
- [Finite State Entropy (FSE)](https://github.com/Cyan4973/FiniteStateEntropy) - A fast entropy coder based on ANS, used in Zstd.

### Dictionary Coders
- [LZ77 and LZ78](https://en.wikipedia.org/wiki/LZ77_and_LZ78) - Dictionary-based lossless data compression algorithms published by Lempel and Ziv.
- [LZW (Lempel-Ziv-Welch)](https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Welch) - A universal lossless data compression algorithm (used in GIF).
- [Deflate](https://en.wikipedia.org/wiki/Deflate) - A combination of LZ77 and Huffman coding (used in ZIP, gzip, PNG).

### Modern Algorithms
- [LZMA (Lempel-Ziv-Markov chain algorithm)](https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Markov_chain_algorithm) - High compression ratio algorithm used in the 7z format.
- [Brotli](https://github.com/google/brotli) - Optimized for web content (Google).
- [Zstandard (zstd)](https://github.com/facebook/zstd) - Fast lossless compression targeting real-time scenarios (Facebook).
- [Snappy](https://github.com/google/snappy) - Aimed at very high speeds and reasonable compression (Google).
- [LZ4](https://github.com/lz4/lz4) - Extremely fast compression algorithm (> 500 MB/s per core).
- [Oodle](http://www.radgametools.com/oodle.htm) - A family of high-performance proprietary compressors widely used in the game industry.

## Integer and Database Compression
*Lightweight techniques for compressing columns of integers and structured data.*

- [Bit-Packing](https://en.wikipedia.org/wiki/Bit-packing) - Storing integers using the minimum number of bits.
- [Frame of Reference (FOR)](https://en.wikipedia.org/wiki/Frame_of_Reference_encoding) - Storing values as offsets from a base value.
- [PForDelta](https://en.wikipedia.org/wiki/PFOR) - Patched Frame Of Reference, handles outliers efficiently.
- [TurboPFor](https://github.com/powturbo/TurboPFor-Integer-Compression) - Extremely fast integer compression library using SIMD.
- [FastPFor](https://github.com/lemire/FastPFor) - A C++ library for fast integer compression using SIMD.
- [StreamVByte](https://github.com/lemire/streamvbyte) - A SIMD-accelerated variable-byte encoding.

## Neural Compression
*Machine learning based codecs for high-efficiency media compression.*

- [CompressAI](https://github.com/InterDigitalInc/CompressAI) - A PyTorch research library and evaluation platform for end-to-end compression.
- [NeuralCompression](https://github.com/facebookresearch/NeuralCompression) - Meta AI's repository for neural compression research.
- [EnCodec](https://github.com/facebookresearch/encodec) - High-fidelity neural audio codec from Meta.
- [DAC (Descript Audio Codec)](https://github.com/descriptinc/descript-audio-codec) - High-quality universal audio tokenizers.
- [TensorFlow Compression](https://github.com/tensorflow/compression) - Google's library for learned data compression in TensorFlow.

## Model Compression (ML Efficiency)
*Techniques to reduce the size of machine learning models.*

- [Quantization](https://huggingface.co/docs/optimum/concept_guides/quantization) - Reducing the precision of model weights (e.g., GPTQ, AWQ, GGUF).
- [Pruning](https://en.wikipedia.org/wiki/Pruning_(decision_trees)) - Removing redundant parameters from a neural network.
- [Distillation](https://en.wikipedia.org/wiki/Knowledge_distillation) - Training a smaller "student" model to mimic a larger "teacher" model.
- [ZipNN](https://github.com/zipnn/zipnn) - Lossless compression for deep learning tensors.

## Media Compression
*Algorithms and standards specifically designed for images, audio, and video.*

### Image
- [JPEG](https://jpeg.org/jpeg/) - Industry standard lossy compression.
- [PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics) - Standard lossless raster-graphics format.
- [WebP](https://developers.google.com/speed/webp) - Lossy and lossless format for the web (Google).
- [AVIF](https://aomediacodec.github.io/av1-avif/) - Next-gen format based on AV1.
- [JPEG XL](https://jpeg.org/jpegxl/) - Modern royalty-free raster-graphics format.
- [BPG (Better Portable Graphics)](https://bellard.org/bpg/) - A high-efficiency image format based on HEVC.

### Audio
- [MP3](https://en.wikipedia.org/wiki/MP3) - Ubiquitous lossy audio format.
- [AAC](https://en.wikipedia.org/wiki/Advanced_Audio_Coding) - Successor to MP3, used in most modern streaming.
- [FLAC](https://xiph.org/flac/) - Standard for lossless audio compression.
- [Opus](https://opus-codec.org/) - Versatile, low-latency royalty-free codec.
- [WavPack](https://www.wavpack.com/) - Hybrid lossless/lossy audio compression.

### Video
- [H.264 / AVC](https://en.wikipedia.org/wiki/Advanced_Video_Coding) - Most widely used video standard.
- [H.265 / HEVC](https://en.wikipedia.org/wiki/High_Efficiency_Video_Coding) - Successor to H.264 with better efficiency.
- [AV1](https://aomedia.org/av1/) - Open, royalty-free video codec.
- [VVC (Versatile Video Coding)](https://en.wikipedia.org/wiki/Versatile_Video_Coding) - The latest H.266 standard.
- [EVC (Essential Video Coding)](https://en.wikipedia.org/wiki/Essential_Video_Coding) - An ISO/IEC standard with a royalty-free subset.

## Specialized Compression
*Techniques adapted for specific types of data.*

- [Time Series Data Compression](https://www.timescale.com/blog/time-series-compression/) - e.g., Facebook's Gorilla.
- [Genomic Compression](https://en.wikipedia.org/wiki/DNA_data_compression) - e.g., CRAM format for DNA.
- [Mesh Compression](https://google.github.io/draco/) - Google Draco for 3D meshes.
- [Executable Compression (UPX)](https://upx.github.io/) - The Ultimate Packer for eXecutables.
- [CLP (Compressed Log Processor)](https://github.com/y-scope/clp) - A tool for compressing and searching logs with very high ratios and fast search speeds.

## Libraries and Tools
*Software implementations and language-specific packages.*

### Command Line Utilities (CLI) & Archivers
- [pigz](https://zlib.net/pigz/) - A parallel implementation of gzip for modern multi-processor, multi-core machines.
- [pbzip2](https://launchpad.net/pbzip2) - A parallel implementation of the bzip2 block-sorting file compressor.
- [pxz](https://github.com/jnovy/pxz) - A compression utility that takes advantage of running LZMA compression of different parts of an input file on multiple cores.
- [lzop](https://www.lzop.org/) - A very fast file compressor which is very similar to gzip but uses the LZO data compression library.
- [ZPAQ](http://mattmahoney.net/dc/zpaq.html) - Free and open source incremental journaling command-line archiver for Windows, Linux and Mac OS/X using PAQ context mixing.
- [squashfs-tools](https://github.com/plougher/squashfs-tools) - Tools to create and extract Squashfs filesystems (highly compressed read-only filesystems for Linux).

### Media Optimization Tools
- [libjpeg-turbo](https://libjpeg-turbo.org/) - JPEG image codec that uses SIMD instructions to accelerate baseline JPEG compression and decompression.
- [mozjpeg](https://github.com/mozilla/mozjpeg) - Improved JPEG encoder from Mozilla, aiming to reduce file sizes without sacrificing quality.
- [pngquant](https://pngquant.org/) - A widely used lossy PNG compressor that significantly reduces file sizes through palette quantization.
- [OxiPNG](https://github.com/shssoichiro/oxipng) - A fast, multithreaded lossless PNG compression optimizer written in Rust.
- [SVGO](https://github.com/svg/svgo) - Node.js tool for optimizing SVG vector graphics files.

### Multi-Language / C / C++
- [zlib-ng](https://github.com/zlib-ng/zlib-ng) - Next-generation zlib, optimized for modern CPUs (AVX, NEON).
- [ISA-L](https://github.com/intel/isa-l) - Intel Intelligent Storage Acceleration Library; extreme performance for x86_64.
- [zstd](https://github.com/facebook/zstd) - Official reference implementation of Zstandard.
- [lz4](https://github.com/lz4/lz4) - Official reference implementation of LZ4.
- [FFmpeg](https://ffmpeg.org/) - The Swiss army knife for audio and video processing.
- [7-Zip](https://www.7-zip.org/) - Open source file archiver with high compression ratios.
- [ImageMagick](https://imagemagick.org/) - Suite for image manipulation and conversion.
- [C-Blosc](https://github.com/Blosc/c-blosc) - A blocking, shuffling and loss-less compression library optimized for numerical and structured data.

### Rust
- [zlib-rs](https://github.com/trifectatechfoundation/zlib-rs) - Pure Rust DEFLATE implementation, often faster than C `zlib-ng`.
- [lz4-flex](https://github.com/PSeitz/lz4-flex) - Extremely fast pure Rust LZ4 implementation.
- [zstd-rs](https://github.com/gyscos/zstd-rs) - High-quality Rust bindings for Zstandard.
- [vortex](https://github.com/vortex-data/vortex) - A modern columnar compression toolkit, a successor to Parquet.
- [flate2](https://github.com/rust-lang/flate2-rs) - The standard Rust library for DEFLATE, supporting multiple backends.

### Go
- [klauspost/compress](https://github.com/klauspost/compress) - Highly optimized Go implementations of Zstd, Snappy, and S2.
- [pgzip](https://github.com/klauspost/pgzip) - Parallel gzip for Go, up to 25x faster.
- [dsnet/compress](https://github.com/dsnet/compress) - A collection of compression algorithms for Go, including Brotli and Bzip2.

### Python
- [python-zstandard](https://github.com/indygreg/python-zstandard) - Feature-rich Zstd bindings with C and CFFI backends.
- [Blosc2](https://github.com/Blosc/python-blosc2) - Optimized for numerical data and NumPy; supports computation on compressed data.
- [python-isal](https://github.com/pycompression/python-isal) - Python bindings for Intel's ISA-L.
- [python-zlib-ng](https://github.com/pycompression/python-zlib-ng) - Drop-in replacement for `zlib` using `zlib-ng`.

## Columnar and Big Data
- [Apache Parquet](https://parquet.apache.org/) - Columnar storage format with advanced encoding and compression.
- [Apache ORC](https://orc.apache.org/) - High-performance columnar storage for Hadoop workloads.
- [BtrBlocks](https://github.com/db-tu/btrblocks) - A high-throughput columnar compression format.

## Hardware Acceleration
*Offloading compression to specialized hardware.*

- [Intel QuickAssist Technology (QAT)](https://www.intel.com/content/www/us/en/architecture-and-technology/intel-quickassist-technology-overview.html) - Hardware acceleration for Deflate and other algorithms.
- [nvCOMP](https://github.com/NVIDIA/nvcomp) - GPU-accelerated lossless compression (NVIDIA).
- [AWS Nitro](https://aws.amazon.com/ec2/nitro/) - Hardware offload for transparent storage compression.

## Benchmarking
*Tools for comparing compression algorithms.*

- [lzbench](https://github.com/inikep/lzbench) - In-memory lossless compression benchmark.
- [Squash](https://github.com/quixdb/squash) - An abstraction library and benchmark for lossless compression.
- [TurboBench](https://github.com/powturbo/TurboBench) - A comprehensive benchmark for many compression algorithms.

## Datasets and Corpora
*Standard datasets for benchmarking compression algorithms.*

- [Silesia Corpus](https://sun.aei.polsl.pl//~sdeor/index.php?page=silesia) - The modern standard for lossless benchmarking (~211 MB).
- [Canterbury Corpus](https://corpus.canterbury.ac.nz/) - A widely used collection for general-purpose benchmarking.
- [Calgary Corpus](http://www.data-compression.info/Corpora/CalgaryCorpus/) - The historical standard for early compression research.
- [ImageNet](https://www.image-net.org/) - Often used for benchmarking lossy and neural image compression.
- [LibriSpeech](https://www.openslr.org/12) - Standard for benchmarking audio and speech codecs.
- [KITTI](http://www.cvlibs.net/datasets/kitti/) - Sensor data (LiDAR, Video) for point cloud and robotics compression.

## Books
- [Data Compression: The Complete Reference](https://www.amazon.com/Data-Compression-Reference-David-Salomon/dp/1846286026) by David Salomon.
- [Introduction to Data Compression](https://www.amazon.com/Introduction-Data-Compression-Khalid-Sayood/dp/0124157963) by Khalid Sayood.
- [Elements of Information Theory](https://www.amazon.com/Elements-Information-Theory-Thomas-Cover/dp/0471241954) by Thomas M. Cover and Joy A. Thomas.
- [Managing Gigabytes](https://www.cs.mu.oz.au/mg/) by Ian H. Witten, Alistair Moffat, and Timothy C. Bell - Compressing and indexing documents and images.

## Seminal Papers
*The theoretical foundations of modern compression.*
- [A Mathematical Theory of Communication (1948)](https://people.math.harvard.edu/~ctm/home/text/others/shannon/entropy/entropy.pdf) - Claude Shannon's foundational paper on information theory.
- [A Method for the Construction of Minimum-Redundancy Codes (1952)](http://compression.ru/download/articles/huff/huffman_1952_minimum-redundancy-codes.pdf) - David A. Huffman's paper introducing Huffman coding.
- [A Universal Algorithm for Sequential Data Compression (1977)](https://ieeexplore.ieee.org/document/1055714) - Jacob Ziv and Abraham Lempel (LZ77).
- [Compression of Individual Sequences via Variable-Rate Coding (1978)](https://ieeexplore.ieee.org/document/1055934) - Jacob Ziv and Abraham Lempel (LZ78).
- [A Technique for High-Performance Data Compression (1984)](https://courses.cs.duke.edu/spring03/cps296.5/papers/welch_1984_technique_for.pdf) - Terry Welch (LZW).
- [Asymmetric Numeral Systems: entropy coding combining speed of Huffman coding with compression rate of arithmetic coding (2013)](https://arxiv.org/abs/1311.2540) - Jarek Duda's paper introducing ANS.

## Journals and Publications
- [IEEE Transactions on Information Theory](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=18) - The premier journal for theoretical aspects of information and coding theory.
- [IEEE Transactions on Image Processing](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=83) - Often features cutting-edge research in image compression.
- [IEEE Transactions on Multimedia](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=6046) - Covers audio, video, and multimedia compression systems.
- [Software: Practice and Experience](https://onlinelibrary.wiley.com/journal/1097024x) - Frequently publishes practical papers on data compression algorithms and implementations.

## Blogs and Web Resources
- [Matt Mahoney's Data Compression Programs](http://mattmahoney.net/dc/) - An incredibly rich repository of compression software, the Large Text Compression Benchmark, and the PAQ series.
- [Fast Compression Blog](http://fastcompression.blogspot.com/) - The personal blog of Yann Collet, creator of LZ4 and Zstandard. Deep dives into compression algorithms and optimizations.
- [cbloom rants](https://cbloomrants.blogspot.com/) - Blog by Charles Bloom (creator of Oodle at RAD Game Tools). Contains extensive technical analysis of compression algorithms.
- [The ryg blog](https://fgiesen.wordpress.com/) - Fabian Giesen's blog, featuring excellent series on entropy coding and data compression.
- [Compression.ru](http://www.compression.ru/index_en.htm) - A large resource on video compression algorithms, video quality measurement, and regular codecs comparisons.

## Engineering Blogs
*Insights into real-world compression at scale from industry leaders.*

- [Meta Engineering: Compression](https://engineering.fb.com/tag/compression/) - Home of Zstandard and infrastructure efficiency deep-dives.
- [Cloudflare Blog: Compression](https://blog.cloudflare.com/tag/compression/) - Low-level optimizations for web and edge performance.
- [Google Open Source Blog](https://opensource.googleblog.com/) - News on Brotli, Snappy, and WebP.
- [Netflix Tech Blog](https://netflixtechblog.com/) - High-scale video encoding and data warehouse compression.
- [Dropbox Tech Blog](https://dropbox.tech/infrastructure) - Creators of Lepton and masters of storage efficiency.

## Courses and Tutorials
- [Data Compression Course (Stanford)](https://web.stanford.edu/class/ee398a/) - Principles and practice of data compression.
- [Information Theory (Khan Academy)](https://www.khanacademy.org/computing/computer-science/informationtheory) - Basic introduction.
- [Colt McAnlis' Data Compression Videos](https://www.youtube.com/playlist?list=PLOU2XLYxmsIKWEJoksyYJvXgQ_LhDngb0) - Engaging series on fundamentals.

## Visualizations and Demos
*Interactive tools to understand how compression works.*

- [Huffman Coding Visualizer](https://huffman-coding-visualizer-pbxfa.ondigitalocean.app/) - Build Huffman trees in real-time.
- [LZ77 Simulator](https://mysimulator.uk/) - Visualize the sliding window and lookahead buffer.
- [LZW Interactive Demo](https://csfieldguide.org.nz/en/chapters/data-compression/lzw-compression/) - See how a dictionary is built dynamically.
- [JPEG Explained](https://pudding.cool/2018/03/compression/) - A beautiful visual essay on how JPEG compression works.
- [BWT Online Encoder](https://calcoolator.eu/burrows-wheeler-transform-encoder-decoder) - Step through the Burrows-Wheeler Transform.

## Community and Conferences
- [DCC (Data Compression Conference)](https://datacompressions.com/dcc/) - The premier academic conference on compression.
- [PCS (Picture Coding Symposium)](https://picturecodingsymposium.org/) - A prestigious, long-running conference focusing specifically on image and video coding.
- [ISIT (IEEE International Symposium on Information Theory)](https://www.itsoc.org/conferences/isit) - The flagship conference of the IEEE Information Theory Society.
- [r/compression](https://www.reddit.com/r/compression/) - Active Reddit community.
- [Encode.su](https://encode.su/) - Forum for compression enthusiasts and developers.

---

## Contributing
Contributions are welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.
