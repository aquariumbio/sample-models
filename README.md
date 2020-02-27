# Aquarium Sample Models

Aquarium Sample properties can be awkward to work with. For example, Primer sequences are stored in our instance as two sub-sequences:

```ruby
primer = Sample.find_by_name("My Primer")
overhang_seq = primer.properties.fetch("Overhang Sequence")
anneal_seq = primer.properties.fetch("Anneal Sequence")
seq = overhang_seq + anneal_seq
length = seq.length
```

The Primer model makes this much easier:
```ruby
needs "Sample Models/Primer"
.
.
.
# Instantiate the Primer by passing an Aquarium Sample (of SampleType Primer)
primer = Primer.new(sample: Sample.find_by_name("My Primer"))

# Get the length of the primer
length = primer.length
```
