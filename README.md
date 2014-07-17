type Bounds struct {
    XMin, YMin, XMax, YMax int32
}
type HMetric struct {
    AdvanceWidth, LeftSideBearing int32
}
type VMetric struct {
    AdvanceHeight, TopSideBearing int32
}
type Glyph struct{
	G			*truetype.GlyphBuf
	F			*truetype.Font
	I			truetype.Index
	verifyCode	*VerifyCode
	text		rune
}
	func (g *Glyph) AdvanceWidth() int32
	func (g *Glyph) Width() int32
	func (g *Glyph) Width() int32
	func (g *Glyph) Height() int32
	func (g *Glyph) LeftMargin() int32
	func (g *Glyph) TopMargin() int32
	func (g *Glyph) HMetric() HMetric
	func (g *Glyph) VMetric() VMetric
	func (g *Glyph) Bounds() Bounds
	func (g *Glyph) hinting() freetype.Hinting
	func (g *Glyph) FontGlyph(size float64, c image.Image) (draw.Image, error)

type VerifyCode struct {
	Width, Height	int
	DPI				float64
	Fonts			[]string
	Size			float64
	Colors, Backgrounds	[]color.Color
	Hinting			bool
	KerningMin,	KerningMax		int
}
	func NewVerifyCode() *VerifyCode
	func (VC *VerifyCode) SetDPI(dpi float64)
	func (VC *VerifyCode) SetColor(c []color.Color)
	func (VC *VerifyCode) SetBackground(b []color.Color)
	func (VC *VerifyCode) SetWidthWithHeight(width, height	int)
	func (VC *VerifyCode) SetFont(font []string)
	func (VC *VerifyCode) SetFontSize(size float64)
	func (VC *VerifyCode) SetHinting(h bool)
	func (VC *VerifyCode) SetKerning(min, max int)
	func (VC *VerifyCode) hinting() truetype.Hinting
	func (VC *VerifyCode) Rander(n int) int64
	func (VC *VerifyCode) RandRange(min, max int) int64
	func (VC *VerifyCode) randColor(c []color.Color) image.Image
	func (VC *VerifyCode) randOpenFont() ([]byte, error)
	func (VC *VerifyCode) xoy(xy string, m, M int) (int, error)
	func (VC *VerifyCode) xywh(x, y string, w, h, W, H int) (dx, dy int, err error)
	func (VC *VerifyCode) Glyph(s rune) (*Glyph, error)
	func (VC *VerifyCode) Draw(text string) (draw.Image, error)
	func (VC *VerifyCode) PNG(text string, w io.Writer) error
	func (VC *VerifyCode) GIF(text string, w io.Writer) error
	func (VC *VerifyCode) JPEG(text string, w io.Writer) error

