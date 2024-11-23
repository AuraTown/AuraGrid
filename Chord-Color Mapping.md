# Building Blocks and Approaches for Chord-Color Mapping

## I. Core Ingredients

### A. Musical Dimensions
1. **Pitch Properties**
   - Individual notes (pitch classes)
   - Root note
   - Bass note
   - Intervals between notes

2. **Chord Properties**
   - Number of unique notes
   - Chord quality (major, minor, etc.)
   - Added tensions (7ths, 9ths, etc.)
   - Voicing/inversions

3. **Harmonic Context**
   - Key relationship
   - Function (tonic, dominant, etc.)
   - Voice leading connections
   - Common tones with other chords

### B. Visual Dimensions
1. **Primary Color Properties**
   - Hue (color wheel position)
   - Saturation (color intensity)
   - Brightness (lightness/darkness)

2. **Secondary Visual Properties**
   - Size/Area
   - Shape
   - Border/Outline
   - Texture/Pattern
   - Position/Spacing
   - Connecting lines/elements

### C. Mathematical Tools
1. **Set Theory**
   - Pitch class sets
   - Interval vectors
   - Forte numbers
   - Set complementation

2. **Graph Theory**
   - Chord networks
   - Voice leading spaces
   - Distance metrics
   - Tonnetz relationships

3. **Spectral Analysis**
   - Frequency ratios
   - Roughness calculations
   - Critical bandwidth
   - Overtone structure

## II. Prior Art & Existing Approaches

### A. Traditional Systems
1. **Scriabin's Color Organ**
   - Direct pitch-to-color mapping
   - Synesthetic associations
   - Limitation: purely sequential mapping

2. **Circle of Fifths Color Mapping**
   - Maps chord roots to color wheel
   - Shows key relationships
   - Limitation: ignores chord quality

3. **Tonnetz-Based Visualization**
   - Shows voice leading relationships
   - Geometric representation
   - Limitation: complex for non-theorists

### B. Modern Research
1. **Psychoacoustic Models**
   - Based on consonance measurements
   - Perceptual foundations
   - Limitation: computationally intensive

2. **Machine Learning Approaches**
   - Learned from musical data
   - Style-specific mappings
   - Limitation: black box nature

## III. Proposed Connection Strategies

### A. Direct Mappings
1. **Root-Based Hue**
   ```
   hue = root_pitch_class * (360/12)
   ```

2. **Complexity to Saturation**
   ```
   complexity = notes.length + extensions.length
   saturation = 100 - (complexity * scaling_factor)
   ```

3. **Consonance to Brightness**
   ```
   consonance = calculate_frequency_ratios(notes)
   brightness = map_consonance_to_range(consonance, 30, 90)
   ```

### B. Relational Mappings

1. **Common Tone Network**
   ```
   for each chord_pair:
       shared_notes = len(chord1.intersection(chord2))
       distance = visual_distance_scale[shared_notes]
   ```

2. **Functional Relationships**
   ```
   function_groups = {
       'tonic': ['I', 'vi'],
       'subdominant': ['IV', 'ii'],
       'dominant': ['V', 'vii°']
   }
   color_families = map_functions_to_colors(function_groups)
   ```

## IV. Proposed Integrated Solution

### A. Primary Visual System
1. **Base Color Assignment**
   - Root note determines base hue
   - Related chords use analogous colors
   - Major/minor affects brightness
   - Extensions reduce saturation

2. **Positioning System**
   - Arrange by common tones
   - Distance reflects voice leading
   - Group by function
   - Connect shared notes

### B. Implementation Example
```python
class ChordColorSystem:
    def __init__(self):
        self.root_colors = generate_root_color_map()
        self.quality_adjustments = {
            'major': {'brightness': +10},
            'minor': {'brightness': -10},
            'diminished': {'saturation': -20}
        }
    
    def assign_color(self, chord):
        base_color = self.root_colors[chord.root]
        quality_mod = self.quality_adjustments[chord.quality]
        extension_mod = -5 * len(chord.extensions)
        
        return Color(
            hue=base_color.hue,
            saturation=base_color.saturation + extension_mod,
            brightness=base_color.brightness + quality_mod['brightness']
        )
    
    def position_chords(self, chord_progression):
        common_tone_graph = build_common_tone_graph(chord_progression)
        return optimize_layout(common_tone_graph)
```

### C. Visual Enhancement Layer
1. **Connectivity Visualization**
   - Line thickness for shared notes
   - Dotted lines for voice leading
   - Arrows for functional progression

2. **Interactive Elements**
   - Highlight related chords
   - Show voice leading paths
   - Display common tones

## V. Evaluation Criteria

1. **Theoretical Validity**
   - Accurately represents musical relationships
   - Consistent with theory principles
   - Mathematically sound

2. **Perceptual Effectiveness**
   - Intuitive understanding
   - Visual clarity
   - Cognitive load management

3. **Practical Utility**
   - Easy to implement
   - Scalable to different contexts
   - Useful for analysis and education

Would you like me to elaborate on any of these components or show how they would specifically apply to your "Toast" chord progression?
